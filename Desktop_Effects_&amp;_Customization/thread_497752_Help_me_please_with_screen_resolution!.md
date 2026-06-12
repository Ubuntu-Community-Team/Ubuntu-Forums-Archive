---
title: "Help me please with screen resolution!"
date: 2007-07-10
forum: Desktop Effects &amp; Customization
---

### Post by djavolo on 2007-07-10
Somebody help me please with screen resolution. When i have been installed Ubuntu 7.04 Feisty Fawn i have screen resolution 1280x1024 but after i have been installed Nvidia  my screen resolution have been changed to 1024x768 and now i cant change back to 1280x1024. 1024x768 i max. Sorry for my bad english and newbie question.

---

### Post by benerivo on 2007-07-10
Have you tried including 1280x1024 in your /etc/X11/xorg.conf file?

---

### Post by djavolo on 2007-07-11
Yes but when i am closing xorg.conf he is sets back to previous config.

---

### Post by mickello on 2007-07-11
Hi, new to the forum. I dont know the answer to this, but exactly the same thing happenned to me. No big deal I guess, but I'd love to fix it. Cheers

---

### Post by waggygee on 2007-07-11
It sounds like you didnt have the root privilages. Add "sudo gedit /etc/X11/xorg.conf" to you terminal (dont include the "s

---

### Post by mpgarate on 2007-07-11
i remember having this problem. it happens when you use an analog plug, rather than digital. ill do a little quoting from [my thread]("http://ubuntuforums.org/showthread.php?t=447097") try this:

> FIXED! Followed these instructions:

Quote:
yes there is a way to fix your resolution: run the command
Code:

sudo dpkg-reconfigure xserver-xorg

from a terminal, and answer all the questions. When you get to the part about what screen resolutions you have, scroll and select 1280*1024.

Then I did a control+alt+backspace, then I noticed the login screen was in 1280 by 1024. I logged in, gave me the old, small resolution. went to system>preferences>screen resolution, and the larger choice was there! If you have specific questions about this, feel free to PM me!

OR you could use [my xorg.conf]("http://mikesubuntu.googlepages.com/etxx11xorg.conf") (I made with a fresh ubuntu install, plus that fix)

---

### Post by Pepse3 on 2007-07-12
Never mind.  Remove my entry.

Pepse.

---

