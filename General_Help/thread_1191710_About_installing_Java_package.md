---
title: "About installing Java package"
date: 2009-06-19
forum: General Help
---

### Post by satimis on 2009-06-19
Hi folks,


Ubuntu 8.04


On visiting a website which required Java 1.1.

Then I followed following URL to check;
How to download and install prebuilt OpenJDK packages
[http://openjdk.java.net/install/](http://openjdk.java.net/install/)

openjdk-6-jre:```

  Installed: (none)
  Candidate: 6b11-2ubuntu2.1
  Version table:
     6b11-2ubuntu2.1 0
        500 http://hk.archive.ubuntu.com hardy-updates/universe Packages
        500 http://security.ubuntu.com hardy-security/universe Packages
     6b09-0ubuntu2 0
        500 http://hk.archive.ubuntu.com hardy/universe Packages

```

Please advise whether it is the right package I need.


According to following links:-

JavaInstallation
[https://help.ubuntu.com/community/JavaInstallation](https://help.ubuntu.com/community/JavaInstallation)

Java
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)


I made a further check;

$ sudo update-java-alternatives -l ```

sudo: update-java-alternatives: command not found

```

Please advise which package I need to install?  TIA


B.R.
satimis

---

### Post by redilyn on 2009-06-19
You need to install the java plugin

Run the following from the terminal
```

sudo apt-get install sun-java6-plugin 

```

---

### Post by satimis on 2009-06-19
> **redilyn said:**
> You need to install the java plugin

Run the following from the terminal
```

sudo apt-get install sun-java6-plugin 

```
Hi redilyn,


Thanks for your advice.  Problem solved.


B.R.
satimis

---

