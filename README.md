# Framework-Design_TestNG

import org.testng.annotations.Test;

import io.netty.buffer.ByteBuf;
import io.netty.handler.codec.base64.Base64;

import org.testng.AssertJUnit;
import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.chrome.ChromeDriver;
import org.testng.Assert;
import org.testng.annotations.*;

public class FirstTestNG {
	public String baseUrl="https://www.saucedemo.com/";
	String driverPath="C:/Users/prateek.krishna/Documents/Automation/selenium/chromedriver_win32/chromedriver.exe";
	public WebDriver driver ;
	
@AfterTest
	public void terminatebrowser() 
	{
		  driver.close();
	}
	  
  @BeforeTest	
  public void launchbrowser() {
	  System.out.println("launching chrome browser");
	  System.setProperty("webdriver.chrome.driver", driverPath);		
	  driver = new ChromeDriver();
	  driver.get(baseUrl); 
	  driver.manage().window().maximize();
	 
	  }
	
  @BeforeMethod
  public void beforemethodvalidate() {
	  System.out.print("Enter details");
  }
  
@Test(priority=0)
  public void validatelogin()
{
	  //String expectedTitle = "Login";
       //String actualTitle = driver.getTitle();
	      //AssertJUnit.assertEquals(actualTitle, expectedTitle);
	driver.findElement(By.id("user-name")).sendKeys("standard_user");
	 driver.findElement(By.id("password")).sendKeys("secret_sauce");
	 driver.findElement(By.id("login-button")).click();
	    }

@Test(priority=1)
public void validatepriority() {
	driver.findElement(By.id("first-name")).sendKeys("Prateek");
 	driver.findElement(By.id("last-name")).sendKeys("Krishna");
 	driver.findElement(By.id("postal-code")).sendKeys("10092");
 	driver.findElement(By.xpath("//input[@class=\"btn_primary cart_button\"]")).click();
 	driver.findElement(By.linkText("FINISH")).click();
 	//driver.close();
}

@AfterMethod
public void aftermethodvalidate()
{
	driver.findElement(By.partialLinkText("Sauce Labs Bike Light")).click();
	driver.findElement(By.xpath("//button[@class='btn_primary btn_inventory']")).click();
 	driver.findElement(By.xpath("//span[@class='fa-layers-counter shopping_cart_badge']")).click();
 	driver.findElement(By.linkText("CHECKOUT")).click();
 	//driver.close();
}

}
