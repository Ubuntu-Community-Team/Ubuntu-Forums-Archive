---
title: "Multi monitor support for Sugar desktop"
date: 2016-02-11
forum: Desktop Environments
---

### Post by rrobb on 2016-02-11
Hello,

Background: Ubuntu 14.04
                     Sugar 0.107
                     Quad monitors (three across with the fourth centrally located above), that work great with the everyday desktop (Unity)


I'd like to set up the Sugar desktop for my kids user accounts so they can play with it.

The default settings in Sugar stretch across all four monitors, making usage pretty annoying (and difficult for youngsters).

I can run it (actually the Live version, which is a full OS based on Fedora) just fine in a VM, but I want to make everything a little more seamless for them. 


Can anyone please point me to the display configuration settings for Sugar?

I know the the Sugar desktop environment runs on a modified X, and I'm hoping I won't have to get in and modify it too much.

I'm not afraid of the terminal, but I am pretty green, so I'll need a link to "configuring displays with the command line for dummies" if it comes to that.


Thanks in advance for any help that you might offer.


Cory

---

### Post by QDR06VV9 on 2016-02-12
Not sure if this is what you are after..
To start the X Configuration Tool, select Main Menu Button (on the Panel) => System Settings => Display, or type the command redhat-config-xfree86 at a shell prompt 
Source: [https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/3/html/System_Administration_Guide/ch-xconfig.html](https://access.redhat.com/documentation/en-US/Red_Hat_Enterprise_Linux/3/html/System_Administration_Guide/ch-xconfig.html)
Also note the multiple page options at the bottom IE: _Prev_ and _Next_

---

### Post by Bucky Ball on 2016-02-12
You could *try* something like arandr. Launch that while in the Sugar desktop and see what it shows. It should let you move the screens around virtually to suit ... with any luck. :| In normal circumstances that should happen. arandr is in the repos and has a GUI.

---

### Post by rrobb on 2016-02-13
Thanks for the help.

Looks like I'll be studying up on some RandR tutorials.




Cory

---

