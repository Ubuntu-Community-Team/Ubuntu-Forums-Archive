---
title: "trouble getting Java to work"
date: 2009-01-05
forum: General Help
---

### Post by jedson3 on 2009-01-05
I have been struggling to install Java in Firefox in my Ubuntu system. 

If I type in “About:plugins” in the Firefox line, I get a long list under the Java section, which includes the following, with lots of updates for many of them:

application/x-java-vm Java Yes 
application/x-java-applet Java Yes
application/x-java-applet;version=1.1 Java Yes
application/x-java-applet;jpi-version=1.6.0_11 Java Yes 
application/x-java-bean;version=1.1 Java Yes

(Yes, indicating that they are enabled.)

jre1.6.0_11 is installed at /usr/java/

libjavaplugin_oji.so
 is in /usr/lib/firefox-3.0.3/plugins

(I navigated to the above two  sites. They really are there.) 

But Java does not seem to work. Does not look like it works on the Java test site, and Hushmail won't do certain things because it needs Java. 

So what might be wrong???

---

### Post by pdtpatrick on 2009-01-05
close firefox and run this.. 

sudo apt-get update;sudo apt-get install ubuntu-restricted-extras.. it should install java (newest version) and all that good stuff.

---

### Post by jedson3 on 2009-01-05
Appreciate your response. PUt those two commands through, and lots of stuff downloaded. But when I try the Java test it still fails to show that it is working. Maybe the test is not working, or there is something I am not understanding.It's a puzzle.
jedson3

---

### Post by ju2wheels on 2009-01-05
What release of Ubuntu are you running?

At a minimum make sure you have updated the default jvm:

```

sudo update-java-alternatives -s java-6-sun

```

---

### Post by jedson3 on 2009-01-06
> What release of Ubuntu are you running?

Hardy 8.04.1  

Tried the update, and it did seem to add some files, but Java still does not seem to be working. I'm using two tests. One is the one on the Java page -- where I think some sort of visual is supposed to appear in the big space in the middle. The other is trying to access my account with Hushmail, which requires Java. Maybe there is a better test, but so far as I can tell Java is still not working. 

jedson

---

### Post by ju2wheels on 2009-01-06
```

gksudo gedit /etc/jvm

```

When you open that it should be something like this (minus the first line for java 6):
```

# This file defines the default system JVM search order. Each
# JVM should list their JAVA_HOME compatible directory in this file.
# The default system JVM is the first one available from top to
# bottom.

/usr/lib/jvm/java-6-sun
/usr/lib/jvm/java-gcj
/usr/lib/jvm/ia32-java-1.5.0-sun
/usr/lib/jvm/java-1.5.0-sun
/usr

```

If /usr/lib/jvm/java-6-sun is missing as the first line in your file, then add it and save it. Then run the update java command again.

---

### Post by jedson3 on 2009-01-07
Opened the etc/jvm file and found just what you said I would -- minus the Java 6 line. Added that line and saved and closed it. Reopened it to be sure the new line was there. It was. Then ran the update again. It seemed to run through its thing as it was supposed to. However, Duke still does not dance on the Java test site, and the Hush still will not load its encription engine. rebooted and cleared the tabs again. Still no dancing Duke. Is a puzzel.

jedson

---

### Post by ju2wheels on 2009-01-07
Are you running 32bit or 64bit Hardy?

For 32bit ensure you have these packages:
```

sudo apt-get install sun-java6-jre sun-java6-plugin

```

For 64bit, there is currently no 64bit browser plugin (well there is one but its not in the repository and is still in alpha or beta so you will have to manual install). In the mean time you can use an alternative java browser plugin (icedtea).
```

sudo apt-get install icedtea6-plugin sun-java6-jre

```

If you have all the packages for your respective architecture then Im out of ideas as to what it could be and maybe someone else that uses those sites/apps can help.

---

### Post by jedson3 on 2009-01-07
It seems to me that when I was installing Java this question came up and somewhere I saw how to check it. I think I had 32 bit and downloaded the Java for 32 bit. But I could have made a mistake. How would I check it?

PS -- Whether this works out or not, I very much appreciate your efforts to help me with this.

Jedson

---

### Post by jespdj on 2009-01-07
```
uname -m
```
if it says x86_64, then you have 64-bit, if it's i686 or i386, then it's 32-bit.

---

### Post by jedson3 on 2009-01-07
The Duke is dancing!!!  So the problem is solved. Thank you all for the help you gave me, and the patience you showed. The problem must have been that I had the wrong plug in for the 32 bit version.

Jedson

---

### Post by fatiberio on 2009-01-30
Hi,
  I am trying to get java plugins working in Firefox 3.0.5 the following way. Rather downloading from SUN, I installed the package openjdk-6-jdk and related packages. The Java JDE and  the VM seem to be working fine, as I can "compile" and view applets.. etc. 

But I am trying to link the  library for plugin in the firefox plugins
directory 
but  
 libjavaplugin_oji.so 

is nowhere to be found. Is it possible to get around this without having to 
reinstall a different package.

Tnx

---

### Post by ju2wheels on 2009-01-30
1. You should really start a new thread as this one was about a related problem but it has technically been solved already and thus to separate your issue from the OP's it should be a new thread.

2. First Id like to ask why you would like to use OpenJDK as opposed to the standard Sun one, not that theres a problem but only because OpenJDK's browser plugin does not support all standard Sun applets/browser applications. Second did you run the java updater after you installed openjdk?

```

sudo update-java-alternatives -s java-6-openjdk

```

---

### Post by Jakob Sundbøl on 2009-02-17
Hello Forum
I am having a related problem. In order to access my webbank, I need my java to work. But it doesn't. I have re-installed firefox, the sun-java6 and the sun-java6-plugin. I have also tried to run the command: 

apt-get install ubuntu-restricted-extras

(which did not install anything, as I already had it, it said). Still it doesn't work. 

I have tried to access the file at /etc/jvm, but there is no such file on my machine. Could that be the reason? 

I have tried to write about:plugins in my firefox, and it claims that a lot of java is there and working: 

Java(TM) Plug-in 1.6.0_10-b33
application/x-java-vm 	Java 		Yes
application/x-java-applet 	Java 		Yes
application/x-java-applet;version=1.1 	Java 		Yes
application/x-java-applet;version=1.1.1 	Java 		Yes
application/x-java-applet;version=1.1.2 	Java 		Yes
application/x-java-applet;version=1.1.3 	Java 		Yes
application/x-java-applet;version=1.2 	Java 		Yes
application/x-java-applet;version=1.2.1 	Java 		Yes
application/x-java-applet;version=1.2.2 	Java 		Yes
application/x-java-applet;version=1.3 	Java 		Yes
application/x-java-applet;version=1.3.1 	Java 		Yes
application/x-java-applet;version=1.4 	Java 		Yes
application/x-java-applet;version=1.4.1 	Java 		Yes
application/x-java-applet;version=1.4.2 	Java 		Yes
application/x-java-applet;version=1.5 	Java 		Yes
application/x-java-applet;version=1.6 	Java 		Yes
application/x-java-applet;jpi-version=1.6.0_10 	Java 		Yes
application/x-java-bean 	Java 		Yes
application/x-java-bean;version=1.1 	Java 		Yes
application/x-java-bean;version=1.1.1 	Java 		Yes
application/x-java-bean;version=1.1.2 	Java 		Yes
application/x-java-bean;version=1.1.3 	Java 		Yes
application/x-java-bean;version=1.2 	Java 		Yes
application/x-java-bean;version=1.2.1 	Java 		Yes
application/x-java-bean;version=1.2.2 	Java 		Yes
application/x-java-bean;version=1.3 	Java 		Yes
application/x-java-bean;version=1.3.1 	Java 		Yes
application/x-java-bean;version=1.4 	Java 		Yes
application/x-java-bean;version=1.4.1 	Java 		Yes
application/x-java-bean;version=1.4.2 	Java 		Yes
application/x-java-bean;version=1.5 	Java 		Yes
application/x-java-bean;version=1.6 	Java 		Yes
application/x-java-bean;jpi-version=1.6.0_10 	Java 		Yes

I am running ubuntu 8.10 on a 32-bit machine. 

Does anybody in here have an idea?

Greetings Jakob

---

### Post by ju2wheels on 2009-02-17
> **Jakob Sundbøl said:**
> Hello Forum
I have tried to access the file at /etc/jvm, but there is no such file on my machine. Could that be the reason? 


That file doesnt exist on Intrepid and is no longer needed. Its only necessary to edit that file if you are running 8.04 Hardy.

Do the following:
```

sudo update-java-alternatives -s java-6-sun

```

Then try the website again.

[Edit] Just so you know, it may not be Java thats the issue at all, especially since its a banking website. I would check their support section and check the list of supported browsers/OS's.

---

### Post by ove overgaard on 2010-12-23
> Hi
I got my java working by leaving the old link to a new link:
In /usr/lib/firefox-addons/plugins you write ln -s /usr/lib/jre1.6.0_17/lib/i386/libnpjp2.so. You have to be root and correct according to Your java edition. Futhermore in /usr/lib You have to write chmod -R ugo+rx. Now Your java and Webbank will work
Kindly Ove

---

