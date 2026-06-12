---
title: "edit grub to add XP Safe Mode in dual boot ?"
date: 2008-12-26
forum: General Help
---

### Post by ieee488 on 2008-12-26
I have Ubuntu 8.10 dual booting with Windows XP.
It used to be at bootup that I can hit F8 and get choice to start XP in Safe Mode.

But it seems that Grub has taken over, because F8 no longer works.

How do I go about adding choice for booting to XP Safe Mode?

---

### Post by jjgy on 2008-12-26
I don't believe it is possible to boot directly into the XP safe mode from Grub, but pressing F8 in the windows bootloader should enable you to select safe mode.

Think of it this way:  Without linux, your computer boots directly to the windows bootloader.  With linux, you may select windows, in which case that same bootloader is called.  That's my understanding at least

---

### Post by Monotoko on 2008-12-26
Yeah...just press windows, then press F8 before windows boots (you have a fraction of a second...so be sure to be quick with F8 ;))

---

### Post by logos34 on 2008-12-26
Can't do it directly from grub, but there is a way, other than F8: add a 'Safe Mode' entry to windows boot.ini (you could even make it the default action)

[http://vlaurie.com/computers2/Articles/bootini.htm](http://vlaurie.com/computers2/Articles/bootini.htm)

But I really don't see the point of doing that--pressing a function key is easy enough

---

### Post by ieee488 on 2008-12-26
Thanks to you all. It looks like I better be darn quick with the F8 key. :)

---

### Post by Herman on 2008-12-27
You might be able to configure the Windows boot loader to bring up it's menu for you and in that case it will pause for a set number of seconds before booting.
You should be able to do that by adding another line to boot.ini, I know that's how it works to add WinGrub.
Surely there would be a line you could type in there that would boot you into safe made without the need to even press F8, I'll see if I can find out for you.

Meanwhile, this link contains information on how to open boot.ini to start editing it, [WinGRUB Page]("http://users.bigpond.net.au/hermanzone/p9.html") , I know you aren't installing WinGRUB, but editing boot.ini will be the same no matter what you're doing.

EDIT: Here's your link, [How to Use and Edit *Boot*.*ini* in Windows XP]("http://www.google.com.au/url?sa=t&source=web&ct=res&cd=3&url=http%3A%2F%2Fvlaurie.com%2Fcomputers2%2FArticles%2Fbootini.htm&ei=18lVSZ-SIJ3gsAPE5sihDQ&usg=AFQjCNFF5RLwXjglcF3XNalEYDvHfo56YQ&sig2=ZtetNOU4Cs8toJzvu7oDsQ") that should solve your problem! :)

EDIT 2: Here's another link I like, just to make sure, [Add *Safe Mode* Startup to the *Boot* Menu ]("http://www.google.com.au/url?sa=t&source=web&ct=res&cd=4&url=http%3A%2F%2Fwww.theeldergeek.com%2Fadd_safe_mode_to_boot_menu.htm&ei=18lVSZ-SIJ3gsAPE5sihDQ&usg=AFQjCNHzqL8Ozw7sXC7ZdnuSqUjSTAPGdg&sig2=JqYGtF-qC2BQNIqnDEwTCQ")

---

