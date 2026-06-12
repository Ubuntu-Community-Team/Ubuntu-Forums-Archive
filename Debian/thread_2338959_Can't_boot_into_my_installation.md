---
title: "Can't boot into my installation"
date: 2016-10-03
forum: Debian
---

### Post by MadleSs on 2016-10-03
Hi guys, 
recently I installed debian 8 alongside windows 10, and I can't boot into Debian... Siply the grub won't start after boot. Is there a possibility to edit grub or get to it from windows? Or I will simply have to reinstall the installation. Thank you :)

---

### Post by yancek on 2016-10-03
A default windows system can't even read a Linux filesystem so that won't work.  You haven't posted enough information for anyone to give you realistic advice.  The best way to get that info is at the site below where you can read about the boot repair software, download and run it and post a link to the output here.  Make sure to select the option to Create BootInfo Sumary and do not try to make any repairs.

 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If you have a pre-installed windows 10, it is most likely UEFI so reading the info at the site below would be useful to you.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by Bucky Ball on 2016-10-03
*Thread moved to **Debian**.*

---

### Post by MadleSs on 2016-10-03
Hi, so here's output from the boot repair 
[http://paste.ubuntu.com/23271355/](http://paste.ubuntu.com/23271355/)

//update
But probably there will be some trouble in bios as well because, now even the windows partition have troubles to start automaticly... I have to select it manualy at boot.

---

### Post by oldfred on 2016-10-03
You show no install of grub to ESP - efi system partition.
Do not know if Debian can install with Secure Boot on in UEFI. 

And how you boot install media is then how it installs. 
May be best to turn off Secure Boot, Turn off Windows fast start up or always on hibernation.
And let Boot-Repair reinstall grub-efi-amd for UEFI boot. Do not install grub-pc for BIOS boot.

---

### Post by MadleSs on 2016-10-03
Hi I tried to change the BIOS to legacy as when I installed the Debian, but the boot repair asked me to put it to UEFI ... so I did and the repair finished with the conclusion that I still boot into Windows only ... This is the output of the boot-repair
[http://paste.ubuntu.com/23271886/](http://paste.ubuntu.com/23271886/)
and it also told me if I can access the windows only (which I'm writting from) I should write this into admin command line 
bcedit/set{bootmgr}path\EFI\debian\grubx64.efi
don't know if I should use the command ... Now in bios I can see debian under EFI it's on the first place before windows, but I only get into the windows partition...

---

### Post by oldfred on 2016-10-03
What brand/model system?
Many require work arounds, some possibly better than others depending on your configuration.

Many do this, which Boot-Repair now can do:
 
 Boot-Repair now creates  bkpbootx64.efi and copies shimx64.efi as bootx64.efi. This is a hard drive default or fallback boot entry in UEFI.
'Use the standard EFI file' in advanced options. 

 As noted on the Arch UEFI site:
On some UEFI systems the only possible way to launch UEFI application on boot (if it does not have custom entry in UEFI boot menu) is to put it in this fixed location: <EFI SYSTEM PARTITION>/EFI/BOOT/BOOTX64.EFI (for 64-bit x86 system)
Users who manually moved efi files around see post #6
[http://ubuntuforums.org/showthread.php?t=2101840](http://ubuntuforums.org/showthread.php?t=2101840)
[http://ubuntuforums.org/showthread.php?t=2219452](http://ubuntuforums.org/showthread.php?t=2219452)
[http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109](http://ubuntuforums.org/showthread.php?t=2221498&p=13012109#post13012109) 

But you may need an entry in UEFI to boot the UEFI hard drive. Some UEFI will  on cold boot, not warm reboot find the /EFI/Boot/bootx64.efi and add an entry. Others require you to add it and then set it first in boot order.

       if ESP sda2, you have to specify drive & partition
sudo efibootmgr -c -d /dev/sda -p 2 -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi" 

Then confirm entry is there & correct:
Check entry is there.
sudo efibootmgr -v

See also:
man efibootmgr

---

### Post by MadleSs on 2016-10-03
My notebook is Lenovo ideapad z510, Windows 10 pro ... 
I wonder if the trouble couldn't be I didn't disable secure boot, but hell I can't find the option anywhere... And what about the command the boot-repair offered me? Should I try it? or it won't help... Or would't it be easier to just reinstall the Debian with some other settings?

---

### Post by oldfred on 2016-10-03
Secure boot on many systems now is "Windows" or "Other". Detail that is Secure boot is that you have to use "Other" to install Windows 7 as Windows 7 does not support UEFI secure boot, but can be installed in UEFI boot mode.

       Lenovo Community Bios Access
[URL="http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2"]http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2
[/URL]
 LENOVO Ideapad 100 Laptop 16.04 Dual Boot  
[https://ubuntuforums.org/showthread.php?t=2336544](https://ubuntuforums.org/showthread.php?t=2336544) 
      
  Lenovo Z510 Laptop & Ubuntu 
[http://ubuntuforums.org/showthread.php?t=2232124](http://ubuntuforums.org/showthread.php?t=2232124) 
    [       ]("http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2")
 Lenovo rename files
[http://ubuntuforums.org/showthread.php?t=2302170](http://ubuntuforums.org/showthread.php?t=2302170) 
    [URL="http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2"]
[/URL]

---

