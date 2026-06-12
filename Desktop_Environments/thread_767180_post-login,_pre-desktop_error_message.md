---
title: "post-login, pre-desktop error message"
date: 2008-04-25
forum: Desktop Environments
---

### Post by snorkytheweasel on 2008-04-25
Xubuntu 7.1
After I log in, but before the desktop appears I get an error message:
Could not look up internet address for is-linuxsrv1

This will prevent xfce from operating correctly

It may be possible to correct the problem by adding is-linuxsrv1 to the file /etc/hosts on your system.

Even though is-linuxsrv1 was already in /etc/hosts, 
I deleted it & saved /etc/hosts
added it back into /etc/hosts & saved

It is now several weeks since it first appeared, the message continues to show up.

The only malfunction that I have observed is that the "switch user" feature doesn't work - it refuses to do anything. Other options on the QUIT menu work OK, and all other functionality of Xfce seems OK.

What is the problem? How can I fix it?

---

### Post by renatore on 2010-01-11
i had the same problem in karmic koala 9.10.

I solved it this way:

it happened after echoing in the root account - i know, i know...
i changed the look of ma hostname or something i don't know what, 
anyway, when i tried to login to xfce it wasn't working allright, got that same message. 
it was connecting to the net and all, but there was no posibility to logout, reboot, shutdown from xfcs, had to login to tty1 as root and kill xorg....

In the gnome, lxde, openbox window managers all worked well and normally.

so, after reading and trying a lot of stuff found here and there
and none of them worked, i looked in my home folder with the 
view of hidden files.

in the folder** .wapi**, i found two files, that had the name of host i 
created during the installation of my xubuntu. i realized, that that 
was the name i have to put in my /etc/hosts file, so i did it, 
rebooted  (dunno if that was necessary, but i deleted my wingdoze 
just this week to put my home on that partition, so i'm a little used to that still :-)) 

After restart, all went normally, xfce started withot that message and with the xfce
session chooser, which was gone during the login's with error.

hope that this will help someone, messing around as i did, trying to change hostname
in the terminal as root, not knowing what it can do.

don't do it in your root account guyz, alright??

:popcorn::lolflag:

---

