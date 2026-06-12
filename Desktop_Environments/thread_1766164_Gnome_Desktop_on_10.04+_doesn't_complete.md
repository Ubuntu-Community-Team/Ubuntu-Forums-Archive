---
title: "Gnome Desktop on 10.04+ doesn't complete"
date: 2011-05-24
forum: Desktop Environments
---

### Post by bbbl67 on 2011-05-24
I had 11.04 installed, and I was having a weird problem when going into the Classic Gnome desktop, since I don't like the new Unity desktop. The problem I was having was that Gnome would start, but it wouldn't complete. Only one panel would come up, but not the main panel where all of the main controls are. I wasn't having any problems getting into Unity, but of course I don't like using it. 

So I tried a hail-mary and reinstalled to an older version of Ubuntu. I went all of the way back to 9.04, since that also includes the Grub-legacy as the default. I then upgraded through the stages from 9.04 to 9.10, and then got to 10.04. Once I got into 10.04, I had the same problem that I was having while using Gnome under 11.04, which is that the desktop didn't complete coming up. It seems to happen only in one user account (mine), but it's not happening in another user account (wife's). But I'm the sys admin, so I need to get my desktop working more than she does!

I'm wondering if after upgrading to 11.04 and Unity, it left something nasty behind in the my local configuration. I use a separate /home filesystem, so it remains intact after any system reinstall. I can't get even get the "Failsafe Gnome" option to work. The only thing that seems to work is a simple old Xterm.

---

### Post by Krytarik on 2011-05-24
Try resetting your panels to their defaults:
```
gconftool-2 --recursive-unset /apps/panel
killall gnome-panel
```
Greetings.

---

### Post by bbbl67 on 2011-05-25
Perfect, that's just what I was looking for. Thanks.

---

