---
title: "Installing WINXP, having Ubuntu 8.10, errormessage"
date: 2009-01-19
forum: General Help
---

### Post by MortenHolst on 2009-01-19
One month ago i bought a new Laptop, and decided to give Ubuntu a go. It worked out ok, but i have now realised, that some essential programs just doesn't work in Wine. 
As I decided to install Windows, I read that it is much easier to start out by installing win, and then Ubuntu afterwards. But as I try to reboot with the WinXP disc in the drive, i'm encountering this blue screen:

[COLOR="Blue"]A problem has been detected and windows has been shut down to prevent damage to your computer.  
 
If this is the first time you've seen this stop error screen, restart your computer.  If this screen appears again, follow these steps:
 
Check for viruses on your computer.  Remove any newly installed hard drives or hard drive controllers.  Check your hard drive to make sure it is properly configured and terminated.  RUN CHKDSK /F to check for hard drive corruption, and then restart your computer.
 
Technical information:
 
***STOP: 0X0000007B (0XF78E2524, BXC0000034, 0X00000000, 0X00000000)[/COLOR]

Do I somehow need to uninstall Ubuntu? I tried looking for an answer on google, but couldn't find a solution.

---

### Post by plucky on 2009-01-19
Probably device driver issue with SATA drives and Windows XP not having the drivers available for SATA devices.


See this [link](http://support.microsoft.com/kb/324103) for further information.


Good Luck

---

### Post by adamlau on 2009-01-19
To be safe, write zeros to the beginning and end of the drive.

---

### Post by MortenHolst on 2009-01-19
Plucky.

Thanks, I think you're right about the SATA drives not being compatible with Winxp. I tried the F6 trick, but it requires a floppy drive, which I don't posses. 
I'll try to google around, but if anyone has a simple solution, please do post it.

Adamlau.
I'm not quite sure what you mean.

---

### Post by MortenHolst on 2009-01-19
Ok, problem solved. 
I went into the BIOS setup and made the HD IDe compatible. This seems to work fine, and I'm now formatting my Hard drive. Hopefully it should be no problem to install the drivers for SATA, when Xp's installed.

---

### Post by adamlau on 2009-01-19
If the resolution above does not work and assuming a standard install:

```
sudo hdparm -i /dev/sda1
```

Will return the model number of your HD. Grab the appropriate low-level formatting utility from the support site of the HD manufacturer and rewrite with zeroes i.e. reformat the boot volume accordingly before proceeding.

---

