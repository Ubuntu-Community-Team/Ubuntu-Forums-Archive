---
title: "Installing the Java Development Kit"
date: 2009-02-18
forum: General Help
---

### Post by Ciwan on 2009-02-18
Hi Guys

Can someone please tell me what commands I need to type into the terminal to get the Java Development Kit installed on my system.

I am learning to program in Java, but before I start I need the JDK installed on my system.

I'd greatly appreciate any help given.

Thank You

---

### Post by taurus on 2009-02-18
You mean something like

```
sudo apt-get update
sudo apt-get install sun-java6-jdk
```

---

### Post by Ciwan on 2009-02-19
Thanks for your reply Taurus

I typed them commands you gave me, and I got a lot of prompts and agreements ..etc I accepted them all.

1) How can I check if the JDK has been successfully installed ?

2) How can I install the latest version of NetBeans (v6.5) through the command line ? Will it be:

```
sudo apt-get netbeans
```

Thank You.

---

### Post by jespdj on 2009-02-19
To check which Java compiler version you have installed:
```
javac -version
```
The version of NetBeans in the Ubuntu repository is old (it is certainly not 6.5). Download NetBeans from the [NetBeans website](http://www.netbeans.org) and run the installer.

---

### Post by konqueror7 on 2009-02-19
the netbeans in the repos are outdated...go to the netbeans site and download 'netbeans-6.5-ml-linux.sh'...after downloading it, type in the terminal,
```
sudo sh netbeans-6.5-ml-linux.sh
```
a gui installer will prompt...

(sometimes when compiz is still enabled, it causes to malfunction the installation)

---

### Post by Ciwan on 2009-02-19
> **konqueror7 said:**
> sometimes when compiz is still enabled, it causes to malfunction the installation

How do I disable Compiz for a couple of minutes, just to make sure the installation doesn't get any errors ?

Thanks Guys

---

### Post by konqueror7 on 2009-02-19
got to System > Preferences > Appearance, 'Visual Effects' tab, then select 'None'...

the only malfunction that it causes is usually that it will not render the components of the installer...but as of 8.10, i think it has been fixed...

---

### Post by Ciwan on 2009-02-19
Thanks konqueror7, that installed Very Smoooothly :)

And thanks to all that helped me get my Programming Environment Sorted.

Your help has been much appreciated.

---

### Post by konqueror7 on 2009-02-19
glad to help...:D

---

