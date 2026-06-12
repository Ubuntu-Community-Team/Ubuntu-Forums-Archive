---
title: "ATI Radeon Mobility M6 + Compiz? (gutsy)"
date: 2008-01-12
forum: Desktop Effects &amp; Customization
---

### Post by jon.reeve on 2008-01-12
I got this new computer with better specs hoping that it'd be able to run compiz faster, but I can't even get it to work at all. :( 

lspci returns: 

01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY

I tried using Envy to install proprietary ATI drivers (manually, since it didn't recognize the chip for some reason), and X wouldn't even load. I checked the tty1 console to find error messages and I got a whole bunch of messages like

serial8250: too much work for IRQ10 

which may not be a related issue for all I know. 

I tried installing xserver-xgl, and this made compiz work but at 3 frames per second or something ridiculous like that.  

Has anyone managed to get compiz to work with this video card?

---

### Post by jon.reeve on 2008-01-12
found the answer at the end of the post here: [http://ubuntuforums.org/showthread.php?p=4125128](http://ubuntuforums.org/showthread.php?p=4125128)

---

