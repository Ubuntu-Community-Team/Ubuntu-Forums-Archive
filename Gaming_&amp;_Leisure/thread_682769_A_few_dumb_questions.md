---
title: "A few dumb questions"
date: 2008-01-30
forum: Gaming &amp; Leisure
---

### Post by AlanGard on 2008-01-30
Hi there, 
I'm working on making a little media center type PC and I need to know how to do a few things. I apologize if this is in the wrong section. 

Is there a way I can map keys to a joystick? I'm trying to use an xbox 360 controller and map the center button to do somthing.

I need to make a session that only loads bare X and the application of my choice. Is there a tutorial out there for that? Thanks.

---

### Post by Scarath on 2008-01-30
Keymap, when you have the controller plugged in, open a terminal and go:

```
showkeys -m
```

this will run a program that shows you the keycode of any key you hit. 

Then use xmodmap to make a new keymap or configure which ever media player you use to repsond to what ever keycode you wish to use. Dont know if it will work with an Xbox controller, i know my numberpad 000 button cannot be mapped.

xmodmap link[1]("http://www.xfree86.org/4.2.0/xmodmap.1.html#toc5")
other key map link [1]("http://ubuntuforums.org/showthread.php?t=535912&highlight=dumpkeys")


Bare X you say? Maybe try other desktop environments? [Openbox]("http://icculus.org/openbox/index.php/Main_Page") is very minimal and very lightweight. Its available in the repos.

---

### Post by zephyrus17 on 2008-09-04
How do you install showkeys?

---

