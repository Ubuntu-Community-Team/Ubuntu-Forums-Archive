---
title: "Screen blanks after recent kernel upgrade"
date: 2005-08-24
forum: Desktop Environments
---

### Post by RikoW on 2005-08-24
Hi everybody,

after the recent linux-image update via the ubuntu update-manager to 2.6.10-5-386 version 34.4 a couple of days ago (and after recovering from the screwed up menu.lst file for grub), I have the annoying problem, that my screen goes blank after about 20 seconds or 1/2 minute of inactivity.

It's not the screensaver! There the times are still set properly, and infact the screensaver gets active after the proper times.

The display is just goes black ....of course comes back after hitting any key.
no such behaviour I had before!!

My screen is a laptop LCD power by ATI Radeon 9000 Mobile with the Xorg drivers.  

Anybody experiencing the same problem or knows how to fix it?

Thanks in advance,

          Riko

---

### Post by felipe on 2005-08-24
Find the Monitor section in your xorg.conf and add the line to disable DPMS, then restart your ubuntu  (you just need to restart /etc/init.d/gdm actually)

Section "Monitor"
        [....]
	Option "DPMS" "false"
EndSection

hope this helps, let us know

---

### Post by RikoW on 2005-08-25
Unfortunately, setting the DPMS option to false made my Xserver crash on start-up :(

Do I need to set something else in some other section? In any way, I don't see why that would have changed because of the linux image update!?

But thanks for the hint, learned something about power management from that. If you use the DPMS option, you can set blank times, shutdown times in the ServerLayout section of xorg. conf.

Section "ServerLayout"
[...]
# options for DPMS true in Monitor section
##      Option "BlankTime"  "10" 
       Option "StandbyTime" "10"
       Option "SuspendTime" "20"
       Option "OffTime" "30"
EndSection


Haven't tested it yet, though!

Cheers,

           Riko

---

### Post by RikoW on 2005-08-25
Now I'm very confused: The blanking of the screen after 1/2 minutes has disappeared today ... as far as I know, I'm running the exact same configuration as before. The settings for "StandbyTime" etc I posted earlier are commented out ...

Oh well, I guess I don't really have to understand that .... :)

---

