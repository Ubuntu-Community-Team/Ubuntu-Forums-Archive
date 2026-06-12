---
title: "gdm does not start after replacing motherboard"
date: 2005-12-10
forum: General Help
---

### Post by RobertLos on 2005-12-10
Hallo,

I had to replace my motherboard Asus A7N8X deLuxe today because there was a problem with powering it up. It kept reseting al the time. Went out and bought an ASUS A7N8X XE. When starting with the new motherboard at first everything seemed to work fine until de gdm was about to come up. It didn't but I was left at the command prompt to log in. Tried to start X with 'startx' but got an errormessage that the AGP card was at a different slot. By editing xorg.conf I could fix this and can come to the graphical user interface by typing startx after logging in.
When rebooted the systems still seems to come up in runlevel 1. I edited /etc/inittab ans changed the runlevel to 5, but that did not work. How can I get ubuntu to start in gnome again?

thanks

Robert

---

### Post by mustang on 2005-12-10
Did you try:

```
 sudo dpkg-reconfigure xserver-xorg 
```

---

### Post by RobertLos on 2005-12-11
did that, but that does not help.  There must be something wrong in the initialisation (/etc/rc5.d or int init.d). Would a reinstall of breezy badger be an option? How to do that without loosing the modules allready loaded? Can I make a dump of everything installed using apt-get?

---

### Post by cjazz on 2005-12-11
What's the result of

sudo dpkg-reconfigure gdm

and selecting gdm?

---

### Post by RobertLos on 2005-12-12
Thanks, that helped.

dpkg -reconfigure gdm said tha gdm was broken. I reinstalled gdm with

sudo apt-get install gdm

Now that graphical gui is loaded at boot time again.

Remains my problem with some dialogue boxes in gdm. gksudo application does prompt for the sudo password, but crashes when i try to enter anything in the box. Also firefox does not work with my defaul account. It crashes as soon as something other than plain html is loaded from the internet. It only works when I invoke firefox with "sudo -H firefox" (which might be unsave).

Robert

---

