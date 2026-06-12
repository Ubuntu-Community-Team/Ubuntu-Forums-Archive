---
title: "Java Runtime Environment"
date: 2006-08-06
forum: Desktop Environments
---

### Post by geovino on 2006-08-06
How do I install Java Runtime Environment?

---

### Post by bmonkey on 2006-08-06
Check this post

[http://www.ubuntuforums.org/showthread.php?t=229306](http://www.ubuntuforums.org/showthread.php?t=229306)

---

### Post by croak77 on 2006-08-06
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by bmonkey on 2006-08-06
> 
sudo apt-get install sun-java5-jre sun-java5-plugin


The above will install the Java runtime environment plus the plugin for firefox

[ [http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper) ] <== excellant guide for ubuntu beginners

---

### Post by zambizzi on 2006-08-06
...and, if you want to go all out and develop w/ the full JDK - do:

```

sudo apt-get install sun-java5-jdk

```

---

### Post by geovino on 2006-08-06
> **bmonkey said:**
> The above will install the Java runtime environment plus the plugin for firefox

[ [http://ubuntuguide.org/wiki/Dapper](http://ubuntuguide.org/wiki/Dapper) ] <== excellant guide for ubuntu beginners

This is what I got:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-java5-jre
davek@davek-desktop:~$

Where can I get it?

---

### Post by zambizzi on 2006-08-06
use synaptic instead so you can enable the right repository, see here:

For JRE alone:
[https://jdk-distros.dev.java.net/ubuntu.html](https://jdk-distros.dev.java.net/ubuntu.html)

For JDK & JRE:
[https://jdk-distros.dev.java.net/ubuntu-dev.html](https://jdk-distros.dev.java.net/ubuntu-dev.html)

---

### Post by geovino on 2006-08-06
installed multiverse repos and then I was able to install java. Thanks for the help:)

---

### Post by tjmoes on 2006-08-07
> **geovino said:**
> This is what I got:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-java5-jre
davek@davek-desktop:~$

Where can I get it?
I dont find synaptic where it is suppose to be or the addpropgram function the java pkg is in a rpm-bin file and i cant seem to get it installed

---

### Post by zambizzi on 2006-08-07
> **tjmoes said:**
> I dont find synaptic where it is suppose to be or the addpropgram function the java pkg is in a rpm-bin file and i cant seem to get it installed

Hit the "Advanced" button in the Add/Remove app...it launches synaptic.

---

### Post by tjmoes on 2006-08-07
I dont have the Add and remove  function that i can see

---

### Post by zambizzi on 2006-08-07
did you try "sudo synaptic"?  Or, if that doesn't work, try "whereis synaptic" in a terminal and launch it wherever it's located.

I just started using Ubuntu this weekend and am not in front of an ubuntu box right now to be any more helpful.

---

### Post by magnoliablossom on 2006-08-07
I used easyubuntu to install my java, flash, and video/sound codecs.  you can find out how here:

[http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_use_Easy_Ubuntu]("http://ubuntuguide.org/wiki/Ubuntu_dapper#How_to_use_Easy_Ubuntu")

Also another good link to have is this:

[http://ubuntuguide.org/wiki/Ubuntu_dapper]("http://ubuntuguide.org/wiki/Ubuntu_dapper")

Which is basically the same one, just at the top of the page. :P

Also, the not having Add/Remove or Synaptic sounds like there's a problem.  What kind of privilages do you have?  For Synaptic I know you have to have root privilages but I'm not certain about Add/Remove.

---

### Post by tjmoes on 2006-08-08
well i got easyubunto but get an error when i 
tar -zxf easyubuntu-3.021.tar.gz say cant open no file but i know its saved console say iot is grrrrrrr

---

### Post by tjmoes on 2006-08-08
i just cant find the add and remove function in the apps menu or system

---

### Post by tjmoes on 2006-08-11
why doesnt my distro have the add and remove functions or the synaptic showing cant find it i got a fresh iso today of 6.06

---

