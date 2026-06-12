---
title: "java doesn't work on firefox but"
date: 2009-01-25
forum: General Help
---

### Post by sPiN1 on 2009-01-25
it works on opera (barley, it's super laggy) i enjoy going on chat sites occasionally and it just doesn't load java on firefox here's a link to the site i go to: [http://www.teenchatcenter.com/flirt.html](http://www.teenchatcenter.com/flirt.html)

when i load it on firefox the box doesn't appear, it doesn't ask for anything to be installed or anything, it's just not there. I know I have java though because it does work on opera. it also does not work on epiphany either. if anyone could help me with this problem i would love them forever!:guitar:

---

### Post by sPiN1 on 2009-01-25
Bump

---

### Post by jespdj on 2009-01-25
Do you have 32-bit or 64-bit Ubuntu? Which version of Java do you have installed?
```
uname -m
```
i386 = 32-bit, x86_64 = 64-bit
```
java -version
dpkg -l | grep java
```

---

### Post by sPiN1 on 2009-01-25
phurion@phurion:~$ uname -m
i686
phurion@phurion:~$ java -version
java version "1.6.0_07"
Java(TM) SE Runtime Environment (build 1.6.0_07-b06)
Java HotSpot(TM) Client VM (build 10.0-b23, mixed mode, sharing)
phurion@phurion:~$ dpkg -l | grep java
rc  gjdoc                                      0.7.8-6                           documentation generation framework for java 
ii  java-common                                0.28ubuntu3                       Base of all Java packages
ii  javahelp2-doc                              2.0.05-3                          Java based help system - contains Javadoc AP
rc  libecj-java-gcj                            3.3.0+0728-5                      Eclipse Java compiler (native library)
ii  sun-java6-bin                              6-07-3ubuntu2                     Sun Java(TM) Runtime Environment (JRE) 6 (ar
ii  sun-java6-jre                              6-07-3ubuntu2                     Sun Java(TM) Runtime Environment (JRE) 6 (ar
phurion@phurion:~$

---

### Post by sPiN1 on 2009-01-26
bump

---

### Post by Mental.Man on 2009-01-26
check the following....

1) Do you have NoScript or Adblock plugins installed for Firefox
2) Type "about : plugins" (No Spaces) in your Firefox address bar and see if it shows anything about Java Plugin 
3) Check if there is a link of "libjavaplugin_oji.so" in your "/usr/lib/mozilla/plugins" -OR- "/usr/lib/firefox-addons/plugins" folder

---

### Post by jespdj on 2009-01-26
> **sPiN1 said:**
> phurion@phurion:~$ uname -m
i686
phurion@phurion:~$ java -version
java version "1.6.0_07"
Java(TM) SE Runtime Environment (build 1.6.0_07-b06)
Java HotSpot(TM) Client VM (build 10.0-b23, mixed mode, sharing)
phurion@phurion:~$ dpkg -l | grep java
rc  gjdoc                                      0.7.8-6                           documentation generation framework for java 
ii  java-common                                0.28ubuntu3                       Base of all Java packages
ii  javahelp2-doc                              2.0.05-3                          Java based help system - contains Javadoc AP
rc  libecj-java-gcj                            3.3.0+0728-5                      Eclipse Java compiler (native library)
ii  sun-java6-bin                              6-07-3ubuntu2                     Sun Java(TM) Runtime Environment (JRE) 6 (ar
ii  sun-java6-jre                              6-07-3ubuntu2                     Sun Java(TM) Runtime Environment (JRE) 6 (ar
phurion@phurion:~$
Ok, you have a 32-bit system. It looks like you have Sun Java 6 installed, but not the browser plug-in. Install the package **sun-java6-plugin**:
```
sudo apt-get install sun-java6-plugin
```
Close and re-open Firefox, and it should work.

---

### Post by sPiN1 on 2009-01-26
> **jespdj said:**
> Ok, you have a 32-bit system. It looks like you have Sun Java 6 installed, but not the browser plug-in. Install the package **sun-java6-plugin**:
```
sudo apt-get install sun-java6-plugin
```
Close and re-open Firefox, and it should work.

thanks this worked! if i could figure out how to give you a thanks i would

---

