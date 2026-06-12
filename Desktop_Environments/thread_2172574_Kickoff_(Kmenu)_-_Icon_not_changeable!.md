---
title: "Kickoff (Kmenu) - Icon not changeable?!?"
date: 2013-09-05
forum: Desktop Environments
---

### Post by Chip88 on 2013-09-05
HI there!


I would like to change one of the icons (computer-laptop.png; see attachment) in Kickoff (Kmenu).


I found a lot of instructions in the internet, how to do it:
I copied all the needed sizes of the new icon (computer_laptop_new.png; see attachment) to */usr/share/icons/oxygen/*.
I even gave root - permission to those files.

Furtermore, I copied the oxygen - theme - folder  to *~/.kde/share/icons*, as described here: [http://www.kubuntuforums.net/showthread.php?26372-HOWTO-create-own-(partial)-icon-theme&p=289332#post289332](http://www.kubuntuforums.net/showthread.php?26372-HOWTO-create-own-(partial)-icon-theme&p=289332#post289332).


Searching for *computer-laptop.png* in the oxygen - theme - folder shows only the new icon (computer-laptop_new.png, see attachment).

I don't know why, but Kickoff doesn't care at all about my changes and the old icon still stays in the Kickoff (see attachment), although I rebooted some times already.

How can I fix this issue and get the new icon to be displayed?!


I'm using:
- KDE 4.10.5
- Ubuntu 13.04
- Kernel: 3.8.0-29-generic .


Thank you in advance for your support & advices!


Regards from Germany!
Chipy

---

### Post by Chip88 on 2013-09-05
Hi there!

I've just found the solution "by accident": It was the CACHE, i. e., I did everything right while changing the icons.

So, here's what to do:
1. **kquitapp plasma-desktop**

2. **/home/user/.kde/cache-PC name/icon-cache.kcache** &#8594; Delete it!

3. To implement the new icons: **plasma-desktop**.

Source: [http://forum.ubuntuusers.de/topic/icons-werden-tlw-nicht-dargestellt/#post-5080207](http://forum.ubuntuusers.de/topic/icons-werden-tlw-nicht-dargestellt/#post-5080207)

Wish you all a nice evening!

Chipy ;)

---

### Post by Erik1984 on 2013-09-05
Thanks for sharing the solution. This also works for the new Firefox logo (introduced with the upgrade from version 22 to 23). It was not updated in Kickoff here but after deleting the icon cache it was.

---

