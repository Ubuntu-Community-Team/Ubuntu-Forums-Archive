---
title: "Frostwire/Java"
date: 2009-05-25
forum: General Help
---

### Post by Legace on 2009-05-25
So, I installed Java on my 64-bit Ubuntu using this guide: [http://www.64bitjungle.com/ubuntu/install-java-jre-160-update-x-on-hardy-as-the-default-java-runtime/](http://www.64bitjungle.com/ubuntu/install-java-jre-160-update-x-on-hardy-as-the-default-java-runtime/)

Java works perfectly. The problem is, that when I try to install the Frostwire debian package, it says that it will install java. I don't won't any other Java than the one currently installed.. 

I need to fake package manager that I have Java
or somehow ignore dependencies. Is this possible?

Thanks

---

### Post by taurus on 2009-05-25
Where did you download frostwire because it should never installs java for you?  It would look for java (Sun version) when you try to run it though.

---

### Post by Legace on 2009-05-25
> **taurus said:**
> Where did you download frostwire because it should never installs java for you?  It would look for java (Sun version) when you try to run it though.

From frostwire.com.

java -version shows:
```
java version "1.6.0_13"
Java(TM) SE Runtime Environment (build 1.6.0_13-b03)
Java HotSpot(TM) 64-Bit Server VM (build 11.3-b02, mixed mode)
```

---

### Post by jespdj on 2009-05-25
> **Legace said:**
> So, I installed Java on my 64-bit Ubuntu using this guide: [http://www.64bitjungle.com/ubuntu/install-java-jre-160-update-x-on-hardy-as-the-default-java-runtime/](http://www.64bitjungle.com/ubuntu/install-java-jre-160-update-x-on-hardy-as-the-default-java-runtime/)
Congratulations on doing that, but please note that that's far more complicated than necessary. You could just have installed the package **sun-java6-plugin** and you'd be done.
```
sudo apt-get install sun-java6-plugin
```
Note that there's a 64-bit browser plug-in included with the version of Sun Java 6 for Jaunty.

---

### Post by taurus on 2009-05-25
> **Legace said:**
> From frostwire.com.

java -version shows:
```
java version "1.6.0_13"
Java(TM) SE Runtime Environment (build 1.6.0_13-b03)
Java HotSpot(TM) 64-Bit Server VM (build 11.3-b02, mixed mode)
```

That command just shows you have java 1.6.0_13 on your machine right now.  All you need is to install frostwire and then run it.

---

### Post by Legace on 2009-05-26
> **taurus said:**
> That command just shows you have java 1.6.0_13 on your machine right now.  All you need is to install frostwire and then run it.

Yeah, but when I double-click on the deb, it says that 6 new packages will be installed, and when I click on details, it has "sun-java-something" listed a couple of times. Should I uninstall the previous java, and install it via synaptic?

EDIT:
I deleted /opt/java and then installed from Synaptic and it seems to be running fine. Thanks.
Note that I had to do following to make Frostwire start:
```
sudo update-alternatives --install "/usr/bin/java" "java" "/usr/lib/jvm/java-6-sun/jre/bin/java" 1
sudo update-alternatives --set java /usr/lib/jvm/java-6-sun/jre/bin/java
```

---

### Post by Soul-Sing on 2009-05-26
or: ```
sudo update-alternatives --config java
```

did you update sun java yourself?

edit: [http://www.64bitjungle.com/ubuntu/in...-java-runtime/](http://www.64bitjungle.com/ubuntu/in...-java-runtime/)
(sorry)

---

### Post by teeleef on 2009-05-29
Hi all,

I solved the Frostwire problem by installing the earlier 4.17 version.


Teeleef

---

