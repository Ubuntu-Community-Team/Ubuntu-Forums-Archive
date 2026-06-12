---
title: "Dr Java problem"
date: 2008-01-22
forum: Education &amp; Science
---

### Post by hlvietlong on 2008-01-22
Hi guys, 

I have a problem running Dr Java on my Dell 6400 Ubuntu Gutsy. It's that whenever I run Dr Java and press any hotkeys (Ctrl O for Open and stuff), it just restarts my X Server for some reasons. I don't know what's the problem and how to fix it. Help me pls!!! I need Dr Java for my CS classes

---

### Post by ghindo on 2008-01-23
I too am in a similar situation - I'm taking a CS course that requires DrJava.

How did you install DrJava?  Are you running it through Wine?

---

### Post by LuCiAn0 on 2008-01-24
I have the same exactly problem. Is there anyone who knows why the xserver just restart with the DrJava is running? I already tried all the versions from DrJava, including the Beta version.... and the problem is still there :(

---

### Post by hlvietlong on 2008-01-24
Hi guys, I think I figured it out. It's because of the jdk. I switched to use jdk 5 for Dr Java and everything is fine, but for jdk 6, icedtea jdk 7 or jdk 1.4, everything got screwed up. I don't know how that works though.
@ghindo: I'm using Dr Java jar file.

---

### Post by thisismalhotra on 2008-01-24
> **hlvietlong said:**
> Hi guys, 

I have a problem running Dr Java on my Dell 6400 Ubuntu Gutsy. It's that whenever I run Dr Java and press any hotkeys (Ctrl O for Open and stuff), it just restarts my X Server for some reasons. I don't know what's the problem and how to fix it. Help me pls!!! I need Dr Java for my CS classes

Dont know if this helps

[http://sourceforge.net/forum/forum.php?forum_id=775007](http://sourceforge.net/forum/forum.php?forum_id=775007)

---

### Post by LuCiAn0 on 2008-02-12
I tried run this with JDK 5.0. DrJava opened ok but when I clicked on preferences to set the tools.jar way, I couldnt see anything. On JDK 5.0 the preferences window doesnt work. It just shows a blank window. I'm not able to configure the compile. :(

---

### Post by LuCiAn0 on 2008-02-12
is there anyone using DrJava on UBUNTU?

---

### Post by LuCiAn0 on 2008-02-25
Ok, problem solved :lolflag::lolflag:

I tried many versions from DrJava and i found one that works great. Just download DrJava Version : 20061025-1556... It works great...

---

### Post by Vladislav Mkrtychev on 2008-06-02
I downloaded DrJava on my ubuntu Hardy. It works.
However, I can only start it up from the shell by using the 
java -jar drjava-stable-20080106-0744.jar command.
Does anybody knows how else can I start it up.
I have tried entering drjava at the prompt
I get : bash: drjava: command not found
Or someone said that I can double click on a .jar file but it just shows me what inside of that .jar file(folder)

Thanks.

---

### Post by vceder on 2008-07-25
I get the X restarting problem on Hardy with Sun JDK 6. 

syslog shows that compiz is segfaulting and if you turn all visual effects off the newer versions of drjava seem to be OK. If you want the visual effects, the 20061025 version appears to work, even with all visual effects turned on.

---

### Post by vceder on 2008-07-25
> **LuCiAn0 said:**
> Ok, problem solved 

I tried many versions from DrJava and i found one that works great. Just download DrJava Version : 20061025-1556... It works great...

The problem is caused by compiz segfaulting, so of course disabling all visual effects corrects the problem also.

In addition, exporting AWT_TOOLKIT="MToolkit" (a fix for java and compiz problems mentioned elsewhere on these forums) before running drjava also seems to take care of the problem.

[INDENT]export AWT_TOOLKIT="MToolkit"[/INDENT]

It's worth noting that this isn't really a DrJava problem, but a problem with compiz and Sun's implementation of Java.

This fix is now listed for this bug on the DrJava forums on SourceForge also. ([http://sourceforge.net/tracker/index.php?func=detail&aid=1925282&group_id=44253&atid=438935](http://sourceforge.net/tracker/index.php?func=detail&aid=1925282&group_id=44253&atid=438935))

Cheers

---

