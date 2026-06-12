---
title: "Can't start GUI after 5.10 Upgrade"
date: 2005-12-30
forum: Desktop Environments
---

### Post by bm5034 on 2005-12-30
Greetings all...

I just upgraded my hp nx9600 laptop to Breezy Badger 5.10.  Everything was running fine under my previous version (Hoary Hedgehog), but now, I receive an error during bootup saying that the xserver could not start.  I am left at a blue screen with extended DOS characters.  My video adapter is an ATI Mobility Radeon X600, with 128 Mb RAM.  I haven't made any hardware changes to my laptop.

I tried to reconfigure xserver with the command:

sudo dpkg-reconfigure xserver-xorg

During this process, my graphics adapter is correctly detected as ATI, and my resolution is set properly, but upon rebooting, I still have the problem.  If I manually select the VESA driver, the GUI loads okay, but I can't utilize my full resolution.

Any suggestions would be appreciated!

Thanks in advance,
Bob

---

### Post by rjwood on 2005-12-30
you may have to reinstall your driver. I'm not familiar with your card but search an ye shall find>  Good Luck!

---

### Post by Irony on 2005-12-30
Same happened here. My solution was to boot into the old 5.04 option (which should still be in the grub menu) and then reboot into 5.10 that sorted the problem.

Alternately you might boot into recovery mode and type startx then reboot once you're in.

I don't know why it worked for me but it did the trick.

---

### Post by thekiller on 2005-12-30
[QUOTE=bm5034]Greetings all...

I just upgraded my hp nx9600 laptop to Breezy Badger 5.10.  Everything was running fine under my previous version (Hoary Hedgehog), but now, I receive an error during bootup saying that the xserver could not start.  
Bob[/QUOTE]

Please post the output of [COLOR="Red"]/var/log/Xorg.0.log[/COLOR] to close out what the problem is.

---

### Post by dcstar on 2005-12-30
[QUOTE=rjwood]you may have to reinstall your driver. I'm not familiar with your card but search an ye shall find>  Good Luck![/QUOTE]
Agreed, but the **first** thing you should do before that is change **all** of the repository entries from "hoary" to "breezy" so you get the Breezy version of the video driver (if there is one), and not just reinstall the Hoary version.

---

### Post by bm5034 on 2005-12-31
Okay, the log file is attached.

I am able to get the display working if I select the VESA driver, but in that case, I can't select the preferred resolution of 1680 x 1050.  Also, when I attempt to reconfigure the xserver parameters, if I let it perform an autodetect of the monitor, it always returns "generic monitor".  Not sure if this is expected behavior for a laptop.

I will attempt to reinstall the ATI driver, but I'm not quite sure of the procedure.  Must I do this from the command prompt?

---

