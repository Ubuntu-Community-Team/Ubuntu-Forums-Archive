---
title: "Some Desktop Effects Not Working on Ubuntu 12.04 LTS"
date: 2013-03-19
forum: Desktop Environments
---

### Post by judedawson on 2013-03-19
Hi All, 

I noticed that my laptop's desktop effect are not working as it should. 

Some do work well ( Super+S, fo example). The others (Ctrl+Alt+Arrow, Alt+Tab) do worl but the display does not show as it should. 

I did a clean install of Ubuntu 12.04LTS (MD5checksum OK) on my laptop a few weeks ago. 

The install went well. My laptop runs fine with the exeption of some destop effects which not working fully. 

Attached is a pdf showing screenshots of what shows on my laptop compared with that of my wife's 6yr Acer Aspire One. 

My laptop details are as follows:

Software:
Release version - Ubuntu 12.04 LTS 32-bit
Kernel Linux: 3.5.0-26-generic
Nautilus Version - Platform Version 3.4.2
GRUB Version - 0.97-29ubuntu66

Hardware:
-Acer Aspire 4750G Laptop
-Intel Core i5, 32bit
-4G DDR3 RAM
-500G HDD (Internal)
-Internal DVD-combo drive
-00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
-01:00.0 VGA compatible controller: NVIDIA Corporation GF119 [GeForce GT 520M] (rev a1)

I have a suspicion that it's got smething to do with the NVidia card. 

I've spent the past 3 weeks scouring the net for an answer but only suceeded at confusing myself :P 

I'm not exactly a newbie but am not an expert either...

Thanks, all.

From,
Jude

---

### Post by judedawson on 2013-03-20
Hi guys, any suggestions or ideas?

---

### Post by tancrackers on 2013-03-21
Check to see if the shortcuts are even the same as when you last used them. Some of mine aren't different (like Super+D).
You may also want to check out CCSM, but be careful! It can break things. After messing with a Compiz tweak, log out and log back in.

---

### Post by TheFu on 2013-03-21
Just a shot in the dark, but did you install the proprietary nvidia drivers from the repository?
Are you certain which GPU is being used?  Don't laptops switch between GPU and built-in based on whether the battery is used or not?

Sorry, I don't really know.

---

### Post by zombifier25 on 2013-03-22
> **TheFu said:**
> Just a shot in the dark, but did you install the proprietary nvidia drivers from the repository?
Are you certain which GPU is being used?  Don't laptops switch between GPU and built-in based on whether the battery is used or not?

Sorry, I don't really know.

Seconded. While the Nouveau driver is pretty good all by itself the proprietary stuff is still objectively better (objectively, since the last time I tried it it never worked for me. Things has changed though)

Laptops that has 2 GPUs usually have a switch that switches between the cards. Make sure it's on NVIDIA.

---

### Post by Isamu715 on 2013-03-23
It seems you're on Unity 2D, that's why the effects don't work. Try logging out, clicking the Ubuntu logo and selecting "Ubuntu" instead of "Ubuntu 2D". As for why your system defaults to the 2D version it may be related to the graphcs card as others have mentioned.

---

### Post by judedawson on 2013-03-27
Hi All,

Thank you very much for your suggestions. 

After a week of troubleshooting, I ended up with the same problem _and_ the touchpad had stopped working :P

So, I backed up my files & did a clean new install of Ubuntu-12.10. 

It works beautifully now :)

From,
Jude

---

### Post by judedawson on 2013-03-27
Err... how do I set this thread as SOLVED, again?

I've forgotten...

---

### Post by Frogs Hair on 2013-03-27
[http://ubuntuforums.org/showthread.php?t=2124016&highlight=mark+threads+solved](http://ubuntuforums.org/showthread.php?t=2124016&highlight=mark+threads+solved)

---

### Post by judedawson on 2013-03-27
Hi Frogs Hair,

Thanks for the link :)

Done.

From,
Jude

---

### Post by chetanbhasin on 2013-05-10
Hi there everybody! Although I see that this thread has been closed, but in case somebody can help me I'm having the same problelm.

I am normally using Unity, but the graphics that I am getting are of Unity 2D. Any idea?

---

