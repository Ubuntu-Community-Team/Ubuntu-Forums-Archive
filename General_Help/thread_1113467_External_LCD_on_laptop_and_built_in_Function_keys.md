---
title: "External LCD on laptop and built in Function keys?"
date: 2009-04-01
forum: General Help
---

### Post by paradigm2 on 2009-04-01
Hello I already put Ubuntu on a older desktop computer I have.  I am so impressed that I am considering fully jumping over and installing it on my Acer Aspire 5100 series laptop as well.

However there is a small worry. The built in screen is broken on this laptop and does not work at all.  It has windows XP home media center on it now and I have to hit Fn+F5 in order to switch to the external LCD that I plug in the back.  I only have to do this once and the next time it boots up using the external.

Will this be an issue when installing Ubuntu?  Will I have access to the same function keys or otherwise will it show on my external LCD by default if I simply lug it in?  I'm worried about ending up stuck with a paper weight if I am not able to get an external LCD working.  That's basically all that is holding me back now. :)  

Is this something built into the BIOS and thus will work in Ubuntu, or is it something special in my OEM version of XP Home Media Center from Acer?

Thank you in advance. :)

---

### Post by FrankT-Qc on 2009-04-01
I wouldn't expect the FN+F? to work, as I have never seen it work on quite a few laptops that I've tried...

On the one I'm using, whenever I boot with an external screen plugged in, it's used by default... Have you tried to boot the live cd with the display plugged in to see if its used at boot ?

If not, what you could do is just make an LiveUSB where you install remote access (ssh, vpn,NX... whatever makes you happy) and there, you would have a chance to do the install and then switch to the external monitor.

After that, the laptop should default to the external monitor (or you google a bit and mess with /etc/X11/xorg.conf) as long as it is plugged in when you boot.

---

### Post by paradigm2 on 2009-04-01
> **FrankT-Qc said:**
> I wouldn't expect the FN+F? to work, as I have never seen it work on quite a few laptops that I've tried...

On the one I'm using, whenever I boot with an external screen plugged in, it's used by default... Have you tried to boot the live cd with the display plugged in to see if its used at boot ?

If not, what you could do is just make an LiveUSB where you install remote access (ssh, vpn,NX... whatever makes you happy) and there, you would have a chance to do the install and then switch to the external monitor.

After that, the laptop should default to the external monitor (or you google a bit and mess with /etc/X11/xorg.conf) as long as it is plugged in when you boot.

Thanks.   I feel silly now. :) I did not even consider the LiveCD. I have one sitting right in front of me now. I will give it a try tonight and report back here so that there is a record for any others that might have this concern.

---

### Post by paradigm2 on 2009-04-03
Just an update for others with related issues who might see this from search.

On my Aspire 5100 series laptop the Fn keys related to the external monitor do work -- at least under the Jaunty Beta.  It appears it is at the BIOS level.  In the BIOS there is also a setting to choose the monitor/display, either "Auto" or "Both".

Kind of interesting now is that I have the reverse problem.  I can't seem to get the failed onboard LCD to turn off and have it only use the LCD.  It stays on showing the garbled screen.  Will have to mess with it.

---

