---
title: "Setting up dualboot [Win8]"
date: 2013-04-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Parapu on 2013-04-11
Good evening guys,

Device: [FONT=Trebuchet MS]Inspiron 17R SE 7720
[/FONT]
I tried setting up my system for over a day by now.
I would like to install both Windows 8 and Ubuntu 12.10, but I couldn't get it how I want it by now.
When I try to install Ubuntu first it does not seem to work at all as Windows will overwrite the partitions from Ubuntu then.
However installing Windows 8 first results in Ubuntu not being able to locate any other OS on the device, so it does not realize that Windows 8 is already installed.
I could install it with the alternative option which does not clear the whole harddrive before installing, but I would like to know if there is a option to set it up so Ubuntu recognizes Windows 8 beforehand.

BIOS settings
[Boot]
Secure Mode: Disabled
Load Legacy Option Rom: Enabled (which I set in order to boot from CD (Windows 8))
Boot List Option: UEFI (not really sure what this option changes as it justs shows/hides the menu keys "Add/Delete Boot Option")

In order to install Ubuntu I add a new boot option (USB) and select the file EFI/Boot/BOOTx64.EFI, this option is then displayed under the category "UEFI boot" in bootmanager.

---

### Post by QIII on 2013-04-11
Englisch wirt hier gesprochen.

Können Sie Ihre Frage ins Englische übersetzen?

Danke sehr!

---

### Post by Parapu on 2013-04-11
I am very sorry :) 
Here we go in English

---

### Post by QIII on 2013-04-11
Thanks.

Not sure if anyone here who knows the answer speaks German.

;)

---

### Post by oldfred on 2013-04-11
Beir is the closest I get to German. 

Was this Dell a Windows 8 system with secure boot? But even if originally Windows 7 it may have a UEFI/BIOS install. 
But the issues are Intel SRT which is a cache to speed Windows and uses RAID which the Ubuntu desktop installer does not see correctly and dual Optimus video which just yesterday nVidia released a beta that supports at least part of it. Normally users install bumblebee.

But if reinstalling yourself, is drive gpt partitioned? Then Windows will only work in UEFI mode. Grub/Ubuntu will work in BIOS or UEFI with gpt partitioned drives. But to dual boot both Windows & Ubuntu have to be the same either UEFI or BIOS boot. And how you boot installer is how it installs.

If drive was gpt and you install Windows in BIOS mode it only overwrites gpt primary partition table. Then Ubuntu's installer sees both primary MBR table and backup gpt partition table so it does not know what to do.

       Installing Ubuntu 12.10 x64 on Dell XPS 13 Alongside Windows from USB New user with Details post 10
[http://ubuntuforums.org/showthread.php?t=2108450](http://ubuntuforums.org/showthread.php?t=2108450)
Dell Inspiron 17R SE -  12.04.2 but otherwise similar to XPS13 above
[http://ubuntuforums.org/showthread.php?t=2125701](http://ubuntuforums.org/showthread.php?t=2125701)

             HOWTO Ubuntu 12.10 x64 Dell XPS 14 (UEFI + Intel Rapid Start Technology + Flashcache), bumblebee - Details
[http://ubuntuforums.org/showthread.php?t=2117166](http://ubuntuforums.org/showthread.php?t=2117166)

    
        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

    
 nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Switchable Graphics is killing my Ubuntu Experience - see post #9
[http://ubuntuforums.org/showthread.php?t=1927317](http://ubuntuforums.org/showthread.php?t=1927317)
Optimus
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
12.10 with bumblebee
[http://ubuntuforums.org/showthread.php?t=2077451](http://ubuntuforums.org/showthread.php?t=2077451)
NVIDIA Confirms It's Working On Optimus Linux Support - Aug 31, 2012
[http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY](http://www.phoronix.com/scan.php?page=news_item&px=MTE3MzY)
Released 319.12 Beta April 2013
[http://www.phoronix.com/scan.php?page=news_item&px=MTM0NzE](http://www.phoronix.com/scan.php?page=news_item&px=MTM0NzE)

---

### Post by Parapu on 2013-04-12
I installed both from UEFI mode now, Ubuntu did not recognize the installed Windows, however I just created a partition from the free disk space left.
I have to chose between Windows boot manager and Ubuntu in boot menu, but I guess it works now.

---

