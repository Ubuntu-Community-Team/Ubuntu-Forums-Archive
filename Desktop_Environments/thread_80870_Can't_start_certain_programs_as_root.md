---
title: "Can't start certain programs as root"
date: 2005-10-23
forum: Desktop Environments
---

### Post by Hanj on 2005-10-23
I recently installed Breezy and soon ran into a weird problem. For some reason I can't start certain graphical programs as root. If I type for instance "sudo gedit", nothing happens. I don't get any error messages in the terminal or anything, it just won't start. First I thought it was a problem with GTK2, because it happens with several other GTK programs, but then I noticed some GTK programs, such as Synaptic are working.

I have no idea how to find out what's causing this (it used to work, so it must be something I changed). Any help is greatly appreciated!

---

### Post by Ampersand on 2005-10-23
Try using
```
gksudo gedit
```
(or whatever program you want to run in the place of gedit).

---

### Post by Hanj on 2005-10-23
I tried that, and nothing happens. No error messages, it just won't start.

---

### Post by Hanj on 2005-10-24
I found out something that may be a clue. When I reboot, the problem is solved for a while, but then it stops working again. Also, there is no processor activity when I try to start a program, it just won't start. Any suggestions?

---

### Post by buldir on 2005-10-24
I have the same problem. No other apps are open and I try to:

1) open the network manager, or
2) change the time zone, or
3) print to postscript in Mozilla web browser

...nothing happens. I waited five minutes...then all the programs open up.

---

### Post by Ampersand on 2005-10-24
Do you happen to have scim installed (for changing keyboard layouts)? I've found that can cause problems with sudo...

---

### Post by Hanj on 2005-10-25
> Do you happen to have scim installed (for changing keyboard layouts)? I've found that can cause problems with sudo...No, scim is not installed.

---

