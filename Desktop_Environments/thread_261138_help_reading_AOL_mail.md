---
title: "help reading AOL mail"
date: 2006-09-19
forum: Desktop Environments
---

### Post by WarrenCarl on 2006-09-19
Hi,

I am very new to Ubuntu, but I am making steady progress toward being a beginner.  We still use AOL for our e-mail.  I thought that this would not be a problem.  I have installed Ubuntu Dapper.
I am running Firefox.  I thought it would be simple to point the browser to [www.aol.com](www.aol.com) and get our AOL mail online.  The AOL website will not allow me to log into AOL because it says I do not have javasoft or do not allow cookies.  In Firefox option, I have checked the box that says use javasoft and I do allow cookies.

I have recently installed various Java programs could any of these be interfering with javasoft or is the Ubuntu version of javasoft different enough that it gives me problems.

Any help would be appreciated.

Thanks.
Warrencarl

---

### Post by umbepo on 2006-09-19
Hello!

I am not too familiar with AOL (luckily:D ), but can you enable POP3? Because if you could, you could use many many many mail clients with ubuntu.

---

### Post by mgmiller on 2006-09-19
It is possible the java you are using is the stock open source java that comes with Dapper.  Sometimes, it's not all that compatible with everything.  Try installing easy ubuntu and having it install sun java.  
[http://easyubuntu.freecontrib.org/]("http://easyubuntu.freecontrib.org/")
I use firefox with dapper to do webmails from lots of sites and have no problems.

To check which javas you have and to switch between them just type this command in a terminal and then you can switch to your preferred java runtime:
```
sudo update-alternatives --config java
```

The one you are looking for should have something like this in it: /usr/lib/j2re1.5-sun/bin/java

If you don't see it, you don't have sun java.  Use easy ubuntu to install it.

---

