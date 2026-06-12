---
title: "How bad are power outages for wubi instalation?"
date: 2009-05-29
forum: General Help
---

### Post by linuxdumby on 2009-05-29
Hi guys, I have ubuntu installed with wubi under windows. I recently had to power off my computer twice for several hours. I know this isnt advised but I had to do it.

What are the dangers when doing this? Is the danger just to the ubuntu instalation itself or does it compromise the whole HD? Does it permanently ruin parts of the hd by creating bad sectors? Or is it just a matter of uninstalling ubuntu/wubi to fix it?

Also when I tried uninstalling ubuntu the grub loader didnt go away. If I use windows instalation cd to do clean install, will that make it go away? I know there are certain programs, commands you can use but I may have to do complete installation of windows anyway so if it can do it automagically it would be best.

---

### Post by KhurramM on 2009-05-29
Simply re-install in case of power failure during installation. Till today I havent seen anybodys hard being ruined by power outage. In older PCs this was a problem, because the powersupply of system used to be not that accurate as it is today.

The clean install will make everything go away ;). Dont worry.

Hope this helps.

---

### Post by jmszr on 2009-05-29
linuxdumby,

Wubi installs Ubuntu into a windows folder, usually a NTFS type of file system, this file system has a known reaction of being unstable in other operating systems like Ubuntu when a hard shutdown happens.

Just boot into windows, then shutdown correctly and then try to boot into ubuntu as normal, everything should work. (From LowSky)

If it doesn't:
                    Boot into Windows, Goto "My Computer", Right click the drive that you have installed Ubuntu in. Click Properties. Select the "Tools" tab and click "check now" under error checking (with Vista you might be asked for administrative rights). Make Sure "Automatically fix file system errors" is checked and click Start. After the checking is done, shut down  by using the start menu (Do Not hard reboot) and  try using Ubuntu now. ( From Ago) - There is also an option for "Scan for and attempt recovery of bad sectors".
                  
You can also accomplish the immediate previous tip by running chkdsk/f for file system errors in Windows and chkdsk/r for both file system errors and bad sectors, then shutting down properly. 

For the grub loader:[http://ubuntuforums.org/showthread.php?t=1173229](http://ubuntuforums.org/showthread.php?t=1173229)

---

### Post by linuxdumby on 2009-05-29
> **jmszr said:**
> linuxdumby,

Wubi installs Ubuntu into a windows folder, usually a NTFS type of file system, this file system has a known reaction of being unstable in other operating systems like Ubuntu when a hard shutdown happens.

Just boot into windows, then shutdown correctly and then try to boot into ubuntu as normal, everything should work. (From LowSky)

If it doesn't:
                    Boot into Windows, Goto "My Computer", Right click the drive that you have installed Ubuntu in. Click Properties. Select the "Tools" tab and click "check now" under error checking (with Vista you might be asked for administrative rights). Make Sure "Automatically fix file system errors" is checked and click Start. After the checking is done, shut down  by using the start menu (Do Not hard reboot) and  try using Ubuntu now. ( From Ago) - There is also an option for "Scan for and attempt recovery of bad sectors".
                  
You can also accomplish the immediate previous tip by running chkdsk/f for file system errors in Windows and chkdsk/r for both file system errors and bad sectors, then shutting down properly. 

For the grub loader:[http://ubuntuforums.org/showthread.php?t=1173229](http://ubuntuforums.org/showthread.php?t=1173229)

Oh, so the issue is with the ntfs not wubi? I thought the issue was wubi needed constant power supply to maintain the integrity of the ubuntu instalation.

Here's the quote from wubi's site

> Hibernation is not supported under Wubi, moreover Wubi filesystem is more vulnerable to hard-reboots (turning off the power) and power outages than a normal filesystem, so try to avoid unplugging the power. An Ubuntu installation to a dedicated partition provides a filesystem that is more robust and can better tolerate such events.Also what do you mean by hard reboot? I managed to shut down properly using ubuntu's menu both times but I had to unplug the power cord after that.

About grub, yes thats the thread Ive read already, but I'm curious as to clean xp install will repair it automagically becos smtimes bootloaders get into mbr which is not deleted during reformat/clean install. True?

---

