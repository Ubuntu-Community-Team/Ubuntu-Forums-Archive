---
title: "problems with SunStudio prerequisite: Java JRE"
date: 2009-04-10
forum: General Help
---

### Post by sbh77 on 2009-04-10
Hi all. I was interested in installing Sun Studio on my Ubuntu laptop (a MacBook Pro - 10.5.6). When I started installing it you initially have to run a prerequisite checker which told me that I needed to update my java jre. I went to Sun and got the jre as a .bin and installed it, sucessfully, except that when I went to the website that automatically checks to see if I had the most current version it said I didn't. The Sun Studio installer also balked when I tried to install it anyways. I don't really know what else to do and have looked around quite a bit. Any ideas?

Thanks a lot!

---

### Post by taurus on 2009-04-10
What version of java is the default on your machine?

```
java -version
```

---

### Post by sbh77 on 2009-04-10
I get the following:

sbh@sbh-laptop:/var/tmp$ java -version
The program 'java' can be found in the following packages:
 * java-gcj-compat-headless
 * openjdk-6-jre-headless
 * j2re1.4
 * kaffe
 * cacao
 * gij-4.1
 * jamvm
 * gij-4.2
 * sablevm
Try: sudo apt-get install <selected package>
bash: java: command not found
sbh@sbh-laptop:/var/tmp$

---

### Post by taurus on 2009-04-10
Try

```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

---

### Post by sbh77 on 2009-04-10
i did the update and then the install, but the latter gave this:

sbh@sbh-laptop:/var/tmp$ sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-bin is already the newest version.
sun-java6-bin set to manually installed.
sun-java6-jre is already the newest version.
sun-java6-plugin is already the newest version.
The following packages were automatically installed and are no longer required:
  gcc-4.1-base libqwt5-qt3
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
sbh@sbh-laptop:/var/tmp$

---

### Post by taurus on 2009-04-10
What's the output of this command?

```
sudo update-alternatives --config java
```
Do you remember where you unpacked the .bin file?

---

### Post by sbh77 on 2009-04-10
sbh@sbh-laptop:/var/tmp$ sudo update-alternatives --config java

There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/lib/jvm/java-6-sun/jre/bin/java
          2    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
          3    /usr/bin/gij-4.2
*+        4    /usr/lib/jvm/java-gcj/jre/bin/java

Press enter to keep the default[*], or type selection number: 
sbh@sbh-laptop:/var/tmp$ 

As for the .bin file.... I assume for the java. they are stored in /var/tmp :

jre-6u13-linux-i586.bin

By the way, what does the last command tell us? 

Thanks much!

---

### Post by sbh77 on 2009-04-10
One other thing, the website from java for verifying the most current installation,

java.com/en/download/installed.jsp?detect=jre&try=1

since I still need to upgrade to version 6 update 13

but also the prerequisite checker in the Sun Studio still says I need to do the same - upgrade java.

Thanks

---

### Post by taurus on 2009-04-10
> 1 /usr/lib/jvm/java-6-sun/jre/bin/java
You want to pick 1 as your default java version.

---

### Post by sbh77 on 2009-04-10
Hi again. I set it to #1 but the website that checks your computer to make sure it is running the most current version still says I am not. Furtermore, when I try to go ahead with the installer for SunStudio12 I still get the same errors:

sbh@sbh-laptop:/var/tmp$ ./prepare_system -C
The following steps are required: java
sbh@sbh-laptop:/var/tmp$ ./prepare_system -s java
error: Failed dependencies:
	glibc >= 2.1.2-11 is needed by jdk-1.5.0_09-fcs.i586
	sh-utils >= 2.0-1 is needed by jdk-1.5.0_09-fcs.i586
	fileutils >= 4.0-8 is needed by jdk-1.5.0_09-fcs.i586
	gawk >= 3.0.4-1 is needed by jdk-1.5.0_09-fcs.i586
	textutils >= 2.0-2 is needed by jdk-1.5.0_09-fcs.i586
	/bin/sh is needed by jdk-1.5.0_09-fcs.i586
sbh@sbh-laptop:/var/tmp$ 

Thanks for the replies and help!

---

### Post by sbh77 on 2009-04-13
Does anyone have any other suggestions? I still don't understand what is wrong and hope someone can figure it out. :)

Thanks

---

### Post by taurus on 2009-04-13
The error message said it needed java-jdk and you have java-jre.  Therefore, you need to install the JDK version.

```
sudo apt-get update
sudo apt-get install sun-java6-jdk
```

---

### Post by sbh77 on 2009-04-17
Thanks again for the suggestion. Unfortunately I get the same error when I check the prerequisites for the SunStudio, as well as when I "verify" the java version using sun's website ( java.com/en/download/installed.jsp?detect=jre&try=1 ), as is stated in the posting #10. I was away for business but am back.... anyone have any other suggestions?  

Thanks much!

---

