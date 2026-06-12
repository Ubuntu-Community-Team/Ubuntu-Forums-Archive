---
title: "How to remove password protection on blank screen"
date: 2007-08-28
forum: Desktop Effects &amp; Customization
---

### Post by mohnish82 on 2007-08-28
Hi,

I have a Dell Inspiron 6400 with Ubuntu 7.04. The problem is that when Ubuntu is up and running, if I close the laptop lid, which is set to blank out the screen, then when I open up the lid again, Ubuntu asks for user password. 

I wish to disable this password prompt on laptop lid re-opening. If you know how to do it, kindly share the solution.

Thanks in advance.

Regards,
Mohnish
=====

---

### Post by LukeCarrier on 2007-08-28
Hello there,

I don't know whether this will be useful, but perhaps clicking
[FONT="Lucida Console"]System >> Preferences >> Screensaver[/FONT]
and un-checking the box that reads 'Lock screen when screensaver is active' may help?

I don't use a laptop so I can't be sure, sorry.

Best regards,
Luke Carrier.

---

### Post by Inxsible on 2007-08-28
Press alt + F2. Type in gconf editor. then go to apps --> gnome-power-manager. Search for lock_on_blank_screen and uncheck it.

if you like the command line, you can do it by```
gconftool-2 --type boolean -s /apps/gnome-power-manager/lock_on_blank_screen false
gconftool-2 --type boolean -s /apps/gnome-power-manager/lock_use_screensaver_settings false
```

---

### Post by digitalbenji on 2007-08-28
I'd just like to comment that the commands posted by Inxsible are badass.

---

### Post by Rupertronco on 2007-08-28
> **digitalbenji said:**
> I'd just like to comment that the commands posted by Inxsible are badass.

Every post I've seen him make has either contributed a great deal to the thread or has been particularly interesting. I wish more people followed that pattern.

---

### Post by Inxsible on 2007-08-28
Thank > **digitalbenji said:**
> I'd just like to comment that the commands posted by Inxsible are badass.
you....
> **Rupertronco said:**
> Every post I've seen him make has either contributed a great deal to the thread or has been particularly interesting. I wish more people followed that pattern.
.....and you.

But honestly, I should also give credit to everyone who helped me out, when I started. Here's a little list of people I'd like to thank...
1)God
2)My parents..without whom I wouldn't be here..
3)Linus Torvalds...without whom we would still be stuck with Windows
4)The Internet
5)The Ubuntuforums community
6)......
7).....

Damn one of them never ending Oscar "thanking" lists !!!:lolflag::popcorn:

---

