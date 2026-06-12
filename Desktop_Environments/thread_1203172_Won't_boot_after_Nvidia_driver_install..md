---
title: "Won't boot after Nvidia driver install."
date: 2009-07-03
forum: Desktop Environments
---

### Post by Ulfgeir on 2009-07-03
I recently installed the 9.04 release of Ubuntu, and all is going fairly well.  However, when I attempted to enable the desktop graphical effects I was prompted to download a proprietary Nvidia driver.
 
I'm running two GeForce 9500 GT cards over SLI.
 
So I installed the driver as prompted (the recommended version -- 180, I think) and then began to reboot, but the system just hangs when it gets to a certain point upon coming back up.
 
I get to see the word "Ubuntu" with the little bar beneath it, but after that it drops the graphical boot screen and leaves me looking at several lines of text, each one followed by an [OK].  The last line says this:
 
"/dev/sda:
     Setting Advanced Power Management level to 0xfe (254)   [OK]"
 
And then it just leaves a blinking cursor a couple spaces below that.  No prompt for command entry or anything.  Anybody know a solution?
 
 
P.S. I'm new to Ubuntu and the Linux scene in general, so my knowledge of how to accomplish things under this OS is pretty limited.

---

### Post by Mayfairy on 2009-07-03
'/dev/sda' part seems to be pointing at your primary SATA HD, if that helps any. 

Quite often (at least with earlier versions) it's stuck on the next part of the bootup, meaning that '/dev/sda' was the last thing it checked and it was ok, and the next one is something it hasn't announced yet. 

Need to find a bootup process list somewhere and check what's coming next to troubleshoot the problem.

---

### Post by Ulfgeir on 2009-07-03
I ran a search online, but couldn't find any kind of detailed enumeration of 9.04's boot process list.  So does anyone know what line comes after the one I listed in my original post?

---

