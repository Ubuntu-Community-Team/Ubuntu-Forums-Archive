---
title: "Setting Environment Variables JAVA_HOME"
date: 2009-04-08
forum: General Help
---

### Post by JasonDFR on 2009-04-08
Would someone please provide instructions or a resource that can help me do the following?

I am attempting to set up Tomcat on my local machine. I found what seems to be a great tutorial, however I don't have enough experience to do the following:

*After you've installed Java, make sure you set your JAVA_HOME environment variable to point to your Java installation, as it's needed not only by Tomcat but also by other tools we use in this article. You'll probably also want to set your PATH variable to point to the bin directory within the Java directory so you have easy access to all the Java tools.*
[http://www.serverwatch.com/tutorials/article.php/2203891](http://www.serverwatch.com/tutorials/article.php/2203891)

Thanks.

---

### Post by Usse on 2009-04-08
this is the command
```
export JAVA_HOME={path to your java installation}
```
but this only set the variable for your current shell.

If you want set the variable for all the shells just put the code in your .bashrc


[https://www.jfire.org/modules/phpwiki/index.php/How%20to%20set%20up%20JAVA_HOME](https://www.jfire.org/modules/phpwiki/index.php/How%20to%20set%20up%20JAVA_HOME)

---

### Post by JasonDFR on 2009-04-08
Great Thanks!

---

### Post by deepakjoy on 2010-10-09
If you want to understand environment variables and the various ubuntu commands for setting and checking their values, then read this : [https://help.ubuntu.com/community/EnvironmentVariables]("https://help.ubuntu.com/community/EnvironmentVariables")

---

