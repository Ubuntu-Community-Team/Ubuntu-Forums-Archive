---
title: "Computer will not shut down completely!"
date: 2009-02-04
forum: General Help
---

### Post by i.gerardus on 2009-02-04
Hi,

I am using ubuntu 8.04.
For some or other reason, all of the sudden, out of the blue, the computer will not shut down properly.

I will shut down the computer through ctrl, alt, delete. Then the little screen comes on, and then I select shut down. The computer will then proceed to quit the software, and ubuntu will log out, and the screen will go pitch black and then go off automatically (this is normally, it does this when there is no 'signal' from th box (hardware). But the problem is, the fan still runs, and the computer still uses electricity. I then have to switch it off at the plug, which is a hassle.

Is this a hardware or software problem? I have gone under PREFERENCES > POWER MANAGEMENT. No luck there.

Thanks for the help.

i.gerardus
Cape Town, South Africa

---

### Post by glotz on 2009-02-04
Maybe there was a kernel update and the newer one thinks that your BIOS is so old it doesn't support [ACPI](http://en.wikipedia.org/wiki/ACPI)?

Drop to a terminal and do **dmesg | grep ACPI**


If that says ACPI is disabled, then do **sudo nano /boot/grub/menu.lst** and find defoptions and append acpi=force there. Then hit Ctrl+X to exit nano and Enter to accept the old filename to save into. Update the menu list with **sudo update-grub** Then reboot and see if it now works.

---

### Post by fragos on 2009-02-04
Many PC's still provide power for some functions after shutdown. For example to allow "wake with LAN" or to provide power to USB ports so devices left plugged in can charge. Your fan may have power until the box temp drops. I use a power strip switch after software shutdown.

---

### Post by i.gerardus on 2009-02-06
Hi. 
Thanks for the help. The bios is still enabled, I checked. 

Will try and leave it, to see if it might go off after a while: ie. when the box temperature drops.

Thanks.

---

### Post by cariboo on 2009-02-06
Open a Applications-->Accessories-->Terminal and at the prompt type:

```
sudo halt
```

It should shut your computer off. I it doesn't press the power switch and hold it until the computer shuts off. You don't have to pull the plug.

Jim

---

