---
layout: post
title: "Dependency Injection and container methods"
date: 2020-06-25 10:22:41 +0500
categories: blog html
---

# Dependency injections and the method to store the repositories .net core 
we created and used abstraction to make the classes loosely coupled. 
    Here, we are going to implement **Dependency Injection** and strategy pattern 
    together to move the dependency object creation completely out of the class
    


# Dependency Ingection
Inject the ICustomerDataAccess .
```cs
    	public class CustomerBusinessLogic
  {
    ICustomerDataAccess _dataAccess;

    public CustomerBusinessLogic(ICustomerDataAccess custDataAccess)
    {
        _dataAccess = custDataAccess;
    }

    public CustomerBusinessLogic()
    {
        _dataAccess = new CustomerDataAccess();
    }

    public string ProcessCustomerData(int id)
    {
        return _dataAccess.GetCustomerName(id);
    }
}

public interface ICustomerDataAccess
{
    string GetCustomerData(int id);
}

public class CustomerDataAccess: ICustomerDataAccess
{
    public CustomerDataAccess()
    {
    }

    public string GetCustomerName(int id) 
    {
        //get the customer name from the db in real application        
        return "Dummy Customer Name"; 
    }
}
```
# Register Dependency injection containers 
  --We have three method to configure the dependency injections repositories customization.
  --Add these method in the starup class *ConfigureServices* as per requiremnets . 

```cs
     public configureService(IService collection service)
     {
        service.AddSinglton(); 
	    service.AddTransient();
	    service.AddScoped();
   }     
```