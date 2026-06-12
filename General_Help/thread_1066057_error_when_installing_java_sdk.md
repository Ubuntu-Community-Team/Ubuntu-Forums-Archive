---
title: "error when installing java sdk"
date: 2009-02-10
forum: General Help
---

### Post by ysbilgin on 2009-02-10
Hi
I started to use ubuntu yesterday :)
I downloaded java_ee_sdk-5_07-linux.bin from java.sun.com and typed 
[PHP]$sh java_ee_sdk-5_07-linux.bin[/PHP] to console. I received [PHP]1: Syntax error: "(" unexpected message.[/PHP]

Do you have any idea?

Thanks... ;)

---

### Post by jespdj on 2009-02-10
Welcome to the forums.

Instead of trying to download and install the Sun Java JDK from Sun's website and installing it manually, just install it from the Ubuntu software repository.

The package you'll want to install is **sun-java6-jdk**. You can install it via the Synaptic package manager (System > Administration > Synaptic Package Manager) or via a terminal command:
```
sudo apt-get install sun-java6-jdk
```
You should always prefer installing software from the Ubuntu repository above installing software manually, because it's easier, the versions from the repository have been tested and work for sure, and you get automatic security updates.

*edit*: Aha, I see you want the Java **EE** SDK. That's not in the Ubuntu repository, as far as I know. First, install the JDK as described above. Then go to [Sun's Java EE download page](http://java.sun.com/javaee/downloads/index.jsp). I think "GlassFish Java EE" (the second package) is the best one to get.

---

### Post by ysbilgin on 2009-02-10
Thank you ;)

---

### Post by ysbilgin on 2009-02-10
> **jespdj said:**
> Welcome to the forums.


*edit*: Aha, I see you want the Java **EE** SDK. That's not in the Ubuntu repository, as far as I know. First, install the JDK as described above. Then go to [Sun's Java EE download page](http://java.sun.com/javaee/downloads/index.jsp). I think "GlassFish Java EE" (the second package) is the best one to get.

Infact i wanted to install jdk but i couldn't found a package including only jdk. I typed the code which you wrote. And my problem has been resolved. Thank you again.

---

