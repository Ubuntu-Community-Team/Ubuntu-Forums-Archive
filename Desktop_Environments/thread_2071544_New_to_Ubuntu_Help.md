---
title: "New to Ubuntu Help"
date: 2012-10-15
forum: Desktop Environments
---

### Post by DoWright on 2012-10-15
I am very excited to be here. First let me explain my system and problem.
      Currently running Win XP on custom made computer, have had VERY little problems for several years. AMD64 1.8Ghz processor with ASUS mother board, 2 internal hard drives. (1-SATA, and 1-IDE), maxed out on RAM. 
      I downloaded both 32bit and 64bit version desktop Ubuntu, then made disc out of each one. I unplugged my 2 internal hard drive to protect them, then plugged in 1 additional IDE hard drive, and formatted it with Win XP, no problem. I then put in my Ubuntu disc, powered down then powered up, it installed with no problem. I powered down, then powered up without disc in DVD drive as program now resides on hard drive. It takes a _LONG_ time to get past BIOS boot up screen, but eventually does and gets to screen that gives the option to select Ubuntu, Ubuntu safe mode, memory test, or Win XP (these are abbreviated descriptions), then I select Ubuntu and it gets to a black screen that looks as though its at a command prompt that says "INITRAFMS>" and wont do anything else. Can any one offer advice, I have tried above procedure with current version 32bit, 64bit, and an earlier version of Ubuntu I down loaded, all with same results.

---

### Post by oldfred on 2012-10-15
Welcome to the forums.

It may be a video issue or other boot option. Have you tried nomodeset? I have to use that on first boot until I install proprietary video drivers for my nVidia card.

What video card are you using?

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

On first boot after install, press e on getting the GRUB bootloader menu. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode), install nVidia driver suggested my Ubuntu

---

### Post by DoWright on 2012-10-16
Thank you reply, my video adaptor is "NVidia GeForce4 MX 4000" according to control panel. 
Newby question.- If I make these changes to enable boot, will this affect my ability to boot into windows, as this will ultimately be a dual boot system, and/or will this make it where I can't boot my computer up at all?
As I have an AMD64 processor, should I install the newest 64 bit Ubuntu or 32 bit to be on safe side, or which version do you recommend? Thank you again for your help in this matter.

---

### Post by oldfred on 2012-10-16
That is an older nVidia and needs the older driver. 

[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

Ubuntu downloads the nVidia driver, but from me that is the current not the legacy. You may be better with just the default nouveau driver?

How much RAM? If less than 3GB, then 32bit probably is better.  I normally suggest 64bit and even run 64bit on my laptop with only 1.5GB of RAM, but it sometimes needs swap and turns grey for a second. The 32bit uses a bit less RAM but 64 bit is faster if you have the RAM to support it.

With dual boot they are separate. It is just that you need to use grub to boot, so you have a choice of which system to boot. Windows boot loader does not give that choice.

---

### Post by spjackson on 2012-10-16
I think that your INITRAMFS> prompt might be due to installing without your other disks connected then reconnecting them.

When the installer configures and installs grub, it writes information about the device and partition to boot from. I suspect that the device number might be wrong once the additional drives are attached.

If you disconnect the 2 additional drives, does it boot Ubuntu OK?

---

