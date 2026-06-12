---
title: "Gnome power manager not detecting battery"
date: 2008-02-25
forum: Dell  Ubuntu Support
---

### Post by b0b4n on 2008-02-25
Ok so from the point that i installed Ubuntu (which has only been a couple weeks so i am a newb when it comes to linux) gnome power manager or linux in general (i think) has been detecting my battery. Yesterday i came home turned on my laptop its wasn't hooked up and it showed that it was running on AC power. and that gnome power manager no longer showed me the battery properties. I also have kpowersave that also doesnt detect the battery.

I found this post [http://ubuntuforums.org/showthread.php?t=321221&highlight=power+manager](http://ubuntuforums.org/showthread.php?t=321221&highlight=power+manager) which told me to do: ```
sudo pkill hald
pkill gnome-power-man
sudo hald
gnome-power-manage
```
this actully worked my gnome power manager and kpowersave found the battery
then i followed the next step on the forum:
> After that the power icon in gnome should be back to normal and work fine until next reboot.
If this is the case, you can modify the boot scripts to make the ACPI daemon start before the HAL daemon. To do so, simply go to /etc/ and look in every rcX.d/ (rc0.d, rc1.d, ... rcS.d) folder. There are many files named with a starting letter, then a 2 digits number, then the rest. Look if in one of these folders the file containing 'acpid' in its name has a greater number than the file containing 'hald' in its name. When this happens, rename the file containing 'acpid' changing the number to the same number of the others rcX.d folders. For example, if in /etc/rc2.d/ there is a 'S50acpid' and a 'S20acpid' file, rename the 'S50acpid' file to 'S10acpid' by typing: sudo mv S50acpid S10acpid.
after that i shut down my computer and the next day i came back and again the  battery was not detected i tried to kill the hall and power manager and boot them back up but this time that didn't work. 

Any ideas how to fix this??? Thanks in advance.

---

