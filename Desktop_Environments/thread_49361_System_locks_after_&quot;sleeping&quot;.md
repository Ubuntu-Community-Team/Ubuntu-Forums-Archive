---
title: "System locks after &quot;sleeping&quot;"
date: 2005-07-16
forum: Desktop Environments
---

### Post by no neck joe on 2005-07-16
I upgraded(?) my kernel to 686 and have since experienced lockups after nonusage. From what I can gather powernowd/cpu frequency scaling is the problem (either that or my pc is pretty lazy... just like me!) and I would like to disable it but I don't know how. 
Any help would be greatly appreciated.

---

### Post by no neck joe on 2005-07-20
What is the unix equivalent to Window's Event Viewer? I'm still locking up every night and I can't figure out what's causing it.

---

### Post by pataphysician on 2005-07-20
[QUOTE=no neck joe]What is the unix equivalent to Window's Event Viewer? I'm still locking up every night and I can't figure out what's causing it.[/QUOTE]

/var/log has a lot of logs in it. perhaps combing through syslog or user.log will help you find what you're looking for. i'm pretty new here, sorry i can't be of more help.

maybe playing with the first three options in /etc/default/acpi-support will help your problem.

the only way i know of to disable frequency scaling (i'm sure there's a better way...) is to kill powernowd. you can do that via rcconf, which can be installed via synaptic.

finally, maybe you can try this?
[http://ubuntuforums.org/showthread.php?t=49112](http://ubuntuforums.org/showthread.php?t=49112)

EDIT:
[http://ubuntuforums.org/showthread.php?t=42129](http://ubuntuforums.org/showthread.php?t=42129)
this looks like a more fully-featured version of rcconf.

---

### Post by no neck joe on 2005-08-03
Desperate bump. 

I completely disabled and removed power management and still locked up every night. I've searched through every log that I can find and as far as I can tell there's no problem yet every morning I have to reboot my machine. 

I get the login prompt with the timer on the side and it's all the way down. I'll put in my password and then it hangs. I left it for 2 hours the other day, no dice.

Help!

---

### Post by az on 2005-08-03
Can you log into a console (CTRL-ALT-F1)?

A shot in the dark:  Perhaps Xscreensaver is trying to use GL or something and that can sometimes make your system crash... depending on your video hardware.

---

