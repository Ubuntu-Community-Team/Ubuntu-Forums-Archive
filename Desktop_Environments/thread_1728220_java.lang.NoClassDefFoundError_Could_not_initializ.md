---
title: "java.lang.NoClassDefFoundError: Could not initialize class sun.awt.X11GraphicsEnviron"
date: 2011-04-13
forum: Desktop Environments
---

### Post by bengwie on 2011-04-13
Hi all,

I am trying to run my automated tests (java) using  selenium through STAF (using root superuser). I have set the DISPLAY  environment variable to ":0.0", and of course the Desktop is available  for ":0.0" (which is for another user, let's call it "user2"). Whenever  running the test, selenium opens up browser successfully in the Desktop  window, but problem arises when it comes to Java Robot's method. It's  throwing this error below:
com.thoughtworks.selenium.SeleniumException:  ERROR: Problem capturing screenshot: java.lang.NoClassDefFoundError:  Could not initialize class sun.awt.X11GraphicsEnvironment
         at  com.thoughtworks.selenium.HttpCommandProcessor.throwAssertionFailureExceptionOrError(HttpCommandProcessor.java:99)
         at  com.thoughtworks.selenium.HttpCommandProcessor.doCommand(HttpCommandProcessor.java:93)
         at  com.thoughtworks.selenium.DefaultSelenium.captureScreenshot(DefaultSelenium.java:719)

-----------------------------------------------------------------------------------------------------------------------------------------------
Few  times it throws below error.

com.thoughtworks.selenium.SeleniumException:  ERROR: Problem capturing screenshot: java.lang.InternalError: Can't  connect to X11 window server using ':0.0' as the value of the DISPLAY  variable.
        at  com.thoughtworks.selenium.HttpCommandProcessor.throwAssertionFailureExceptionOrError(HttpCommandProcessor.java:99)
         at  com.thoughtworks.selenium.HttpCommandProcessor.doCommand(HttpCommandProcessor.java:93)
         at  com.thoughtworks.selenium.DefaultSelenium.captureScreenshot(DefaultSelenium.java:719)
         at  com.zimbra.qa.selenium.framework.core.ExecuteHarnessMain$ResultListener.getScreenCapture(ExecuteHarnessMain.java:646)
         at  com.zimbra.qa.selenium.framework.core.ExecuteHarnessMain$ResultListener.onConfigurationFailure(ExecuteHarnessMain.java:700)
         at  org.testng.internal.Invoker.runConfigurationListeners(Invoker.java:1608)
         at  org.testng.internal.Invoker.handleConfigurationFailure(Invoker.java:286)
         at  org.testng.internal.Invoker.invokeConfigurations(Invoker.java:186)
         at  org.testng.internal.Invoker.invokeConfigurations(Invoker.java:92)
         at org.testng.SuiteRunner.privateRun(SuiteRunner.java:274)
         at org.testng.SuiteRunner.run(SuiteRunner.java:193)
        at  org.testng.TestNG.createAndRunSuiteRunners(TestNG.java:910)
        at  org.testng.TestNG.runSuitesLocally(TestNG.java:879)
        at  org.testng.TestNG.run(TestNG.java:787)

---------------------------------------------------------------------------------------------------------------------
Things  that I observed:
1. When I simulated the similar case over ssh, that  I ssh to the box using root super user, then redirect the DISPLAY to  ":0.0" (Desktop logged in as user2), earlier I was having the exact same  problem, but I fixed it by doing this: [http://ubuntuforums.org/showthread.php?t=1099777](http://ubuntuforums.org/showthread.php?t=1099777)  .
2. Through java, I have tried setting the environment variables to  make sure when running the tests from STAF, these environment variables  are set just like when logging in through SSH:

Map<String,  String> envVars = new HashMap<String, String> ();
envVars.put("STAFCONVDIR",  "/usr/local/staf/codepage");
envVars.put("STAF_INSTANCE_NAME",  "STAF");
envVars.put("SHELL", "/bin/bash");
envVars.put("CLASSPATH",   "/usr/local/staf/lib/JSTAF.jar:/usr/local/staf/samples/demo/STAFDemo.jar:/usr/local/staf/lib/JSTAF.jar:/usr/local/staf/samples/demo/STAFDemo.jar");
envVars.put("DISPLAY",  ":0.0");
envVars.put("USER", "root");
envVars.put("EDITOR",  "vi");
envVars.put("HOME", "/root");
envVars.put("PWD", "/root");
envVars.put("TERM",  "xterm");
envVars.put("PATH",  "/usr/local/staf/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games");
envVars.put("LOGNAME",  "root");
envVars.put("LD_LIBRARY_PATH",  "/usr/local/lib:/usr/lib:/lib:/usr/local/staf/lib");
envVars.put("LANG",  "en_US.UTF-8");
set(envVars);


where set method  definition:
public static void set(Map<String, String> newenv)  throws Exception {
   Class[] classes =  Collections.class.getDeclaredClasses();
   Map<String, String>  env = System.getenv();
   for(Class cl : classes) {
      if("java.util.Collections$UnmodifiableMap".equals(cl.getName()))  {
         Field field = cl.getDeclaredField("m");
          field.setAccessible(true);
         Object obj = field.get(env);
          Map<String, String> map = (Map<String, String>) obj;
          map.clear();
         map.putAll(newenv);
      }     
    }
}

------------------------------------------------------------------------------------------------------------------------------------------------------------------------

I  figure there must be some of you who might know how to solve this  problem. Any help will be appreciated. Thanks.

---

### Post by bengwie on 2011-04-13
Additional Information:
1. I could open up a browser and also start selenium by having DISPLAY set to :0.0
2. I have also tried "xhost +" from the Desktop to give permission to all host clients
 
Result:
Still no luck.

---

