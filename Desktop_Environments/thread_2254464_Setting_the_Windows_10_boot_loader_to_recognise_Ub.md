---
title: "Setting the Windows 10 boot loader to recognise Ubuntu - possible?"
date: 2014-11-27
forum: Desktop Environments
---

### Post by Sslaxx on 2014-11-27
So, I'm currently futzing about with the Win10 tech preview, and at the moment to boot into Linux I have to use the BIOS boot device selector - Ubuntu doesn't pick up the non-MBR-using hard drive Win10 uses (and Win10 won't install as bootable on the HDD Linux is on). So I guess my best bet is to try and get the Win10 boot loader to give the option to boot into Linux - if this is possible. Is it? And if so, how?

Thanks.

---

### Post by user1397 on 2014-11-27
did you disable secure boot?

---

### Post by grahammechanical on 2014-11-27
> [COLOR=#000000]So I guess my best bet is to try and get the Win10 boot loader to give the option to boot into Linux[/COLOR]

I would not bet on it. You will lose your "money." This might be correctable,

> [COLOR=#000000]Ubuntu doesn't pick up the non-MBR-using hard drive Win10 uses [/COLOR]

Have you run?

```
sudo update-grub
```

Regards.

---

### Post by Sslaxx on 2014-11-27
Windows 10 no longer supports booting from (or installing onto) MBR formatted hard drives, and the new GPT format is not (currently) supported by Ubuntu/GRUB. So running update-grub does precisely nothing. And yes, I do believe secure boot is disabled.

---

### Post by yancek on 2014-11-27
There was a convoluted method to boot Linux from the xp bootloader which used boot.ini, might be possible with manual file configuration.  Some people use EasyBCD on windows which is basically a GUI front end to modify the modified Grub (Grub4Dos modified with NeoGrub) to run on windows.  Do you have Ubuntu installed as UEFI boot?  I installed the windows tech preview in VirtualBox which would be anothe option.  It's obviously beta and I would not use a working computer to install a test system.

---

### Post by oldfred on 2014-11-27
Is Linux in BIOS/CSM boot mode.?
UEFI & BIOS are not compatible, once you start booting in one mode you cannot change, you have to reboot and choose from UEFI boot menu. Some system also require you to turn on/off UEFI or CSM mode, others will auto switch as it knows how you installed. You should also be then able to use one time boot key to choose which to boot.

If both systems are UEFI then there are work arounds, not sure what now still works with Windows 10.
       Windows 10 Dual boot on Toshiba works - sudodus
[http://ubuntuforums.org/showthread.php?t=2246751&p=13137869#post13137869](http://ubuntuforums.org/showthread.php?t=2246751&p=13137869#post13137869)

---

