---
title: "Setting PATH for J2SE"
date: 2006-02-17
forum: Desktop Environments
---

### Post by cobbweb on 2006-02-17
Hi, 
   I'm trying to set the path for my J2SE but don't really know how. This is where the files are stored on my computer: 

 /Java/J2SE/jdk1.5.0_06/bin

 Little confused and would like to start programming in Java asap. Thanks, any help is wanted.. 

  Cobbweb

---

### Post by taurus on 2006-02-17
In your ~/.bashrc (if you don't have one, create it), add

PATH=$PATH:/Java/J2SE/jdk1.5.0_06/bin
export PATH

---

### Post by cobbweb on 2006-02-17
[QUOTE=taurus]In your ~/.bashrc (if you don't have one, create it), add

PATH=$PATH:/Java/J2SE/jdk1.5.0_06/bin
export PATH[/QUOTE]


just curious, whats a bashrc? and where should it be created? Thanks for the help BTW

 Cobbweb

---

### Post by gibson on 2006-02-17
This is not really recommended for ubuntu though as there is a java, javac  etc in /usr/bin and you should use the update-alternatives to set these up properly.

I would recommend getting automatix to install and setup the java for you - that is what i did, it is much cleaner.

it also lets you install LOADS of other usefull stuff and is a breeze to use.

[http://www.ubuntuforums.org/showthread.php?t=114251](http://www.ubuntuforums.org/showthread.php?t=114251)



hope this helps

---

