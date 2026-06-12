---
title: "Sun Java did not install"
date: 2010-04-12
forum: Desktop Environments
---

### Post by SwaroopKunduru on 2010-04-12
Hello All,

I did not see java installed in Ubuntu 10.04 so I try to install the latest java by giving the following command.
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin 
[sudo] password for swaroop: 

After entering password I got the following and java not installed in it.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sun-java6-bin

Please help me with steps to install java in Ubuntu10.04

Thanks in advance.
Regards,

Swaroop Kunduru.

---

### Post by 3rdalbum on 2010-04-13
> **SwaroopKunduru said:**
> Hello All,

I did not see java installed in Ubuntu 10.04 so I try to install the latest java by giving the following command.
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin 
[sudo] password for swaroop: 

After entering password I got the following and java not installed in it.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package sun-java6-bin

Please help me with steps to install java in Ubuntu10.04

Thanks in advance.
Regards,

Swaroop Kunduru.

The sun-java6-bin package is definitely available in Ubuntu 10.04's Partner repository. Have you got all the repositories enabled? Have you refreshed your package list?

Go to System > Administration > Software Sources and check that the first four checkboxes are ticked on the first tab. Go to the "Other Software" tab and make sure that the entry marked:

```
http://archive.canonical.com/ubuntu lucid partner
```

is ticked. This one contains Java. Click the Close button and you'll be asked if you want to reload the package list. You do.

If it doesn't ask, then go into Synaptic Package Manager and hit the Reload button, this will load up the package list.

---

### Post by SwaroopKunduru on 2010-04-13
Thanks for the help. It saved a lot of my time.

Regards,

Swaroop Kunduru.

---

### Post by SwaroopKunduru on 2010-04-13
Problem!!!!!!!

Sun java installed but when I try to compile I am getting following
> 
javac Test.java
The program 'javac' can be found in the following packages:
 * openjdk-6-jdk
 * ecj
 * gcj-4.4-jdk
 * gcj-4.3
Try: sudo apt-get install <selected package>


What to do now? I checked in synaptic package manager it shows that sun-java6 is installed.

Sorry for asking again. Please help me again.

Regards,

Swaroop Kunduru.

---

### Post by SwaroopKunduru on 2010-04-13
I am sorry, I was assuming sun-java6-bin is JDK but it is not. I have to install sun-java6-jdk to install JDK.

Regards,

Swaroop Kunduru.

---

