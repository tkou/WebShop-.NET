WebShop Case MVC.

Remarks:
The application has two data sources : an XML file with the articles for the article retrieval
and the SQL server database for the rest of the functionality. 

Paging of the articles in homepage was implemented not only on the WebGrid(client side)
but also the server side data source (XML). 

Since the use of just "Models" is not consider anymore best practice,
the application separates the DTO's to models and viewmodels.
When a DTO has impact on the UI is considered a "ViewModel" and does not apply any business logic, but 
when it is related to business functionality or just for transferring data this class is considered a "Model".
For that reason the WebShop.MVC assembly (our MVC project) has only "ViewModels" classes.

Additional Technologies used:
ASP.NET Membership for user registration/login functionality.
Data Access : Entitiy Framework 
For the Database creation EF was used with the code first approach,
all tables were generated through the creation of Entities (classes) in WebShop.Data assembly.
Apart from LINQ to entities/ LINQ to objects also LINQ to XML was used,
for the retrieval of articles(products) from the XML file.
The application also uses Unity (Microsoft.Practises.Unity) for resolving dependencies during the
dependency injection pattern for loose coupling.
More specifically, constructor injection has been implemented between the following targets :
service -> controller : a contract (Interface) is mapped to a Service class where the contract is passed as parameter (injected) in the controller constructor.
facade -> service :  a contract (Interface) is mapped to a Facade class where the contract is passed as parameter (injected) in the service constructor.

Architectural Perspective:
The application at this moment is composed of three assemblies
WebShop.Data
WebShop.Business
WebShop.MVC

WebShop.MVC referencing WebShop.Business referencing WebShop.Data

WebShop.Data : is where the data access takes place, the database is exposed in a DbContext class via Entity Framework.
WebShop.Business : is where the Business logic is applied to Entities or other related Business models.
WebShop.MVC : is where the UI is displayed where business entities or models are transformed to ViewModels via "Service" classes
and every ViewModel impacts on a View (Strongly Typed View) having as strong type the ViewModel class.
