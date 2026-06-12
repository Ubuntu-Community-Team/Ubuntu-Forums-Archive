---
title: "java installed beautifully but Chat room crashes and frostwire wont start"
date: 2006-07-24
forum: Desktop Environments
---

### Post by Luthy on 2006-07-24
The Java installed good, but when i go into my java chat room it crashes my firefix browser. And Frostwire wont start. I uninstalled Frostwire and re-installed but nothing. Please help?

---

### Post by Jagot on 2006-07-24
After installing Java, did you set it as the default.  If not:

```
sudo update-alternatives --config java
```

---

### Post by Luthy on 2006-07-24
luthy@luthy-desktop:~$ sudo update-alternatives --config java

There are 6 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.1
*+    2        /usr/lib/jvm/java-gcj/jre/bin/java
      3        /usr/bin/cacao
      4        /etc/alternatives/kaffe-system/bin/java
      5        /usr/bin/gij-wrapper-4.0
      6        /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

Press enter to keep the default[*], or type selection number:
I choose number 2 but my browser is still crashing! And frostwire still dont work. :-(

---

### Post by Jagot on 2006-07-24
You need number 5 - the proper Sun Java implementation.

---

### Post by jISh on 2006-07-25
5? No, need option #6, the SUN JRE. It's the one that will be compatible with those applications.

---

### Post by Jagot on 2006-07-25
Yep - sorry - late here - eyes blurry . . .

Anyway, yeah - that's the one which should be compatible with all the applications you need.

---

### Post by Luthy on 2006-07-25
Thank you worked wonderfully. <3 you guys!

---

### Post by leona on 2006-10-04
hi there, 
Hope you can help, having the same trouble here, but I only have 3 option
      1        /usr/bin/gij-wrapper-4.1
      2        /usr/lib/jvm/java-gcj/jre/bin/java
 +    3        /usr/lib/j2se/1.4/bin/java
this isn't right, I DO have java 1.5 installed, but no option for it, how can I add options?

---

### Post by leona on 2006-10-24
Hi. to anyone else having trouble with java chat, this problem can also be caused by a rouge font package that Ubuntu installed, if yo remove this packge this problem will be solved.

sudo apt-get remove ttf-gujarati-fonts

I found this out while googling for this problem, just in case anyone else is struggling like I was :)

---

### Post by The Darkness on 2006-11-10
SWEET!!!!!!!!
That fixed my java chat problem as well

---

### Post by iPirates on 2007-03-27
Niice, that line fixed my problem!

sudo apt-get remove ttf-gujarati-fonts

I couldn't understand why frostwire was crashing when I tried entering my nickname in for the chat portion...
thanks!

---

### Post by Buddha443556 on 2007-04-19
> **leona said:**
> Hi. to anyone else having trouble with java chat, this problem can also be caused by a rouge font package that Ubuntu installed, if yo remove this packge this problem will be solved.

sudo apt-get remove ttf-gujarati-fonts

I found this out while googling for this problem, just in case anyone else is struggling like I was :)

Yep that worked - used the Adept GUI but still worked. Thanks!

---

### Post by whistlerspa on 2007-04-20
Thanks guys  - fixed my Frostwire problem as well  - I had an option for sun-java 6 that worked

** 4    /usr/lib/jvm/java-6-sun/jre/bin/java**

Wp

---

### Post by johnnyxhawk on 2008-03-21
Hi i am having the same issues. 
I am a beginner so i am unsure where go to execute these  commands.  How do i get rid of that font pack or select the default
thanks

---

