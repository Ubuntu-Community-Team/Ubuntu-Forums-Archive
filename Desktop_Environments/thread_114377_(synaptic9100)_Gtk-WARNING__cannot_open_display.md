---
title: "(synaptic:9100): Gtk-WARNING **: cannot open display:"
date: 2006-01-08
forum: Desktop Environments
---

### Post by ipp3l1 on 2006-01-08
Okay, I tried to search for similar case, but didn't find anything that helped. 

This is my problem :

If I try to run synaptic, disks, Users&Groups or any other Adminstrative tool, it wont start. If I try to run synaptic in terminal, it gives me this error :

(synaptic:9100): Gtk-WARNING **: cannot open display:

I've tried to run it with sudo, and also as a root user, but no help.

I'm not really sure what **precisely** I did wrong, but I messed up with some xorg settings and one (can't remember what](*,) ) installer crashed and I think it's been like that ever since. If I remeber right, the setup asked me many keyboard&mouse settings and some other stuff, I was trying to get my TV-OUT working. Being a Linux-noob, I've messed up with million things not exactly knowing what I've been doing...

Anyway, if someone can help me out, I'd really appreciate. If I have to reinstall my system, that does'nt mind, cause I anyway have to do that thus I want to install Ubuntu to another partition... But it would be great to know, is it possible to undo all this sh*t I've done.

Thanks in advance :)

---

### Post by amohanty on 2006-01-08
Try:

> sudo dpkg-reconfigure xserver-xorg

This will allow you to reconfigure your xserver settings. Choose defaults and restart X using Ctrl+Alt+Backspace

HTH
AM

---

### Post by ipp3l1 on 2006-01-08
Nope, it didn't work. All that happened was, that my Screens refresh rate dropped from 85 to 60 :( 

I think I'll reinstall Ubuntu tomorrow...

---

### Post by amohanty on 2006-01-08
Post the output of :

> echo $DISPLAY

Then try the following:

> sudo synaptic --display :<display number>
 replace display number by the number returned by the previous command (usually 0 or 20). Then reinstall xserver

eg:
> sudo synaptic --display :0

HTH
AM

---

