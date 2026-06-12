---
title: "Really Small Fonts"
date: 2008-05-12
forum: Desktop Environments
---

### Post by Insignius on 2008-05-12
Hi.

I installed Ubunutu over the weekend. It's the third time I've tried and this is the farthest I've gotten--such that I'm pretty certain I'm going to stick with it. 

Anyway, the box I put it on is almost six years old.  While it still gets the job done, I noticed it was a little sluggish with Gnome is I thought I'd try Xfce to see if there was any difference. 

I installed the Xubuntu desktop and everything went fine, except after I logged in, the fonts were small.  Really small.  So small that I can't read them even if I hold a magnifying glass up next to the monitor. 

I found several other threads on the same problem, and they suggested a few fixes, the problem is everything is so small I can't tell what the heck I'm doing.

Any ideas?

---

### Post by morgengenuss on 2008-05-12
you could switch to a console via alt+f2 and change the dpi-setting in xorg.conf
[URL="http://gentoo-wiki.com/HOWTO_Set_DPI_(Dots_Per_Inch)"]
this article in the gentoo wiki[/URL] should basically explain what you have to do.

hope that helps.

---

### Post by Insignius on 2008-05-13
Thanks.

That did fix the problem (after a complete reinstall and some messing around with the NVIDIA config)

Except now the gdm screen is completely off the screen. All I can see is the Ubuntu symbol and the "X" of Xubuntu in the lower right-hand corner. 

:mad:

---

### Post by morgengenuss on 2008-05-14
have you had a look in /etc/gdm/gdm.conf ?

if not, especially look at this line: command=/usr/bin/X -br -audit 0

you could try to change it to something like this: command=/usr/X11R6/bin/X -br -audit 0 -dpi 120

---

