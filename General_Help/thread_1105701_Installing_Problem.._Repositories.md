---
title: "Installing Problem.. Repositories??"
date: 2009-03-25
forum: General Help
---

### Post by Eric the Red on 2009-03-25
Hello I'm using Edgy 6.10 and I need to do 1 more last thing before I upgrade in 1 months time. 

This would be to run

```

someone@theServer:~/Desktop$ sudo apt-get install sun-java6-jdk tomcat5.5 tomcat5.5-admin tomcat5.5-webapps

```

However, when I try this I get,

```

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package tomcat5.5

```

I'm pretty new to Linux in General but is this a so called "Repository Issue"? What must I do to fix this so that the software can be found?

Any help would be appreciated.

---

### Post by danking12 on 2009-03-25
My guess is that Tomcat 5.5 wasn't released or supported when Edgy was released. Unfortunately the Ubuntu staff has removed the repository list for Edgy on this website packages.ubuntu.com (or I can't find it).

I looked at Dapper (the release before Edgy) and the version in that release was Tomcat 5. You can see the package names here:

[http://packages.ubuntu.com/search?keywords=tomcat&searchon=names&suite=dapper&section=all](http://packages.ubuntu.com/search?keywords=tomcat&searchon=names&suite=dapper&section=all)

One question I have is, are the other Tomcat 5.5 packages being found? If so that is odd.

---

### Post by dcstar on 2009-03-25
> **Eric the Red said:**
> Hello I'm using Edgy 6.10 and I need to do 1 more last thing before I upgrade in 1 months time. 
........
Any help would be appreciated.

7.04 is no longer supported, 6.10 is nearly gone, you better upgrade soon:

[http://www.ubuntu.com/news/ubuntu610end-of-life](http://www.ubuntu.com/news/ubuntu610end-of-life)

---

### Post by zvacet on 2009-03-25
@ **Eric the Red**

Edgy is not supported anymore.More bad news.You can not upgrade because Feisty is unsupported too.If you have some important files or data back it up and do fresh install of some supported versions like Hardy,Intrepid...

---

