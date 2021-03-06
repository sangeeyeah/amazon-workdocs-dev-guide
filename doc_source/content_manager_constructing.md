# Constructing Amazon WorkDocs Content Manager<a name="content_manager_constructing"></a>

Amazon WorkDocs Content Manager can be used for both administrative and user applications\. For user applications, a developer must construct Amazon WorkDocs Content Manager with anonymous AWS credentials and an authentication token, whereas IAM credentials must be used without an authentication token for administrative applications\.

The following code demonstrates how to initialize Amazon WorkDocs Content Manager for user applications using Java or C\#\.

**Note**  
For administrative applications, the Amazon WorkDocs client must be initialized with IAM credentials and the authentication token most be omitted in subsequent API calls\.

Java:

```
AWSStaticCredentialsProvider credentialsProvider = new AWSStaticCredentialsProvider(new AnonymousAWSCredentials());

AmazonWorkDocs client = AmazonWorkDocsClient.builder().withCredentials(credentialsProvider).withRegion("region").build();

ContentManager contentManager = ContentManagerBuilder.standard().withWorkDocsClient(client).withAuthenticationToken("token").build();
```

C\#:

```
AmazonWorkDocsClient client = new AmazonWorkDocsClient(new AnonymousAWSCredentials(), "region");
ContentManagerParams params = new ContentManagerParams
{
WorkDocsClient = client,
AuthenticationToken = "token"
};
IContentManager workDocsContentManager = new ContentManager(param);
```