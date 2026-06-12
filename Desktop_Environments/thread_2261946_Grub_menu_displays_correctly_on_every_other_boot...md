---
title: "Grub menu displays correctly on every other boot..."
date: 2015-01-22
forum: Desktop Environments
---

### Post by iansan on 2015-01-22
Reading the forums it appears others are having similar grub issues to mine, which looks to be the result of a recent system update. On a successful boot the grub menu will appear and I can boot into Ubuntu. Now if I restart the computer the grub menu appears to start to load as the purple color is drawn on the screen, but no menu appears and then the screen goes black/blank after a second.

At this point no amount of waiting solves the problem - the grub menu never appears. Pressing the enter key doesn't load Ubuntu but I am able to trigger a system reboot with ctrl-alt-del. Rebooting after a failed grub boot then causes grub to boot correctly on the next attempt. I tried repairing grub but the issue remained. I also wiped my Ubuntu drive, used gparted to delete all partitions including boot, and did a fresh install of Ubuntu 14.04 64-bit. The problem remains.

This is an annoying issue that I'd love to resolve.

---

### Post by oldfred on 2015-01-22
Just to see what is where:
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

And what is your brand/model system and what video card/chip?

Do not reboot with ctrl-alt-del or power switch unless that is the only alternative.

       
 Never force shutdown your system. Use Alt+SysRq R-E-I-S-U-B instead. (For newer laptops they don't bother adding the SysRq print to the key, but it's the same as the PrtScr key)

   Holding down Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is.
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.
[xhttp://kember.net/articles/reisub-the-gentle-linux-restart/](xhttp://kember.net/articles/reisub-the-gentle-linux-restart/)

---

### Post by iansan on 2015-01-23
My Boot Info summary report is at [http://paste.ubuntu.com/9831342/](http://paste.ubuntu.com/9831342/). My desktop has this hardware:

Motherboard: MSI Z77A-G43
CPU: Intel i5-3570K
RAM: 12GB Crucial Ballistix Sport DDR3 (was 16GB during installation, had a stick go bad and throw memtest errors, just removed but has made no difference for this boot issue)
Video card: Onboard VESA: GM204 Board (MSI GeForce GTX 970 Gaming is installed but I haven't reinstalled the Nvidia drivers after this latest installation)
Hard drive: OCZ Vertex 4 SSD (I unplugged my Windows 7/SanDisk SSD during installation so grub does not show it)

I'll keep that keyboard shortcut in mind. Unfortunately on my keyboard I'd need three hands to hold the alt and print screen keys down while typing in that sequence :)

---

### Post by oldfred on 2015-01-23
Your system is new enough to be UEFI, but you have installed in BIOS/MBR.

Do you perhaps still have UEFI on in UEFI/BIOS? So then it tries to boot in UEFI mode, does not find the efi partition and reboots back into BIOS boot mode?
The two modes are not compatible and system has to reboot to switch modes.

I do not see anything specifically wrong with install.

---

### Post by iansan on 2015-01-23
I checked my BIOS and the boot option is set to "Legacy+UEFI". I've never changed this value in the past so it must default to that. I changed it to "UEFI" and rebooted and was dropped into an EFI shell that I'm unfamiliar with. I changed the boot option back to "Legacy+UEFI" and am having the original behavior of a successful grub boot every other time.

---

### Post by oldfred on 2015-01-23
Then there is no Legacy only boot option?

---

### Post by iansan on 2015-01-23
No unfortunately there are only the "Legacy+UEFI" and "UEFI" options in the BIOS. But I never had this grub boot problem until recently which is strange.

---

### Post by oldfred on 2015-01-23
Not sure that log files would show anything as that is after grub and I do not think grub writes any log files.

There is the log file viewer. And /var/log/dmesg is the log of boot. You can look for errors.

 [https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

 [http://www.cyberciti.biz/tips/linux-shutdown-command-and-logfile.html](http://www.cyberciti.biz/tips/linux-shutdown-command-and-logfile.html)

---

### Post by iansan on 2015-01-24
Here's what I have:

```
cat /var/log/dmesg | grep error
[    0.629769] nouveau: probe of 0000:01:00.0 failed with error -22
[    9.687038] EXT4-fs (dm-1): re-mounted. Opts: errors=remount-ro
```

---

### Post by oldfred on 2015-01-24
With Intel nouveau would not be used. And your new nVidia card need much newer Linux to work with nouveau.

       The GTX 970/980 Maxwell GPUs Light Up With Nouveau On Linux 3.19
[http://www.phoronix.com/scan.php?page=news_item&px=MTg4NTg](http://www.phoronix.com/scan.php?page=news_item&px=MTg4NTg)
NVIDIA GeForce GTX 970/980: Windows vs. Ubuntu Linux Performance 2015 note versions ppas used to update
[http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell900_winlin&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell900_winlin&num=1)

---

### Post by iansan on 2015-01-24
Hmm ok. That doesn't explain the grub errors though correct?

---

### Post by oldfred on 2015-01-24
It could be related to video and/or shutdown.

Grub tries to use default video and if that is an issue then it may not work correctly.

And grub retains info on abnormal shutdown and tries to use defaults on next boot.

---

### Post by iansan on 2015-01-25
So it sounds like my best option would be upgrading to Ubuntu 14.10 then?

---

### Post by oldfred on 2015-01-25
Not sure if that would make a difference or not.
I prefer to create another 10 or 20GB / partition and install, just to test. That way you keep your current mostly working install.
Either way you reinstall be sure to have good backups.

---

### Post by iansan on 2015-01-27
That's a good idea to test with a smaller partition. Thanks for your help!

---

