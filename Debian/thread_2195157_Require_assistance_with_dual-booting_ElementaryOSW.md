---
title: "Require assistance with dual-booting ElementaryOS/Windows 8.1"
date: 2013-12-22
forum: Debian
---

### Post by doncoyoteee on 2013-12-22
Hi there,

A couple weeks back I discovered Elementary OS and I loved it. The problem was that for work-purposes I need to be able to use Adobe prgorams and therefore need Windows installed. The obvious conclusion I came to was to set up a dualboot with Elementary OS and Windows 8.1; this did not go as easily as many told me it would. The problem I have is that when I boot to Elementary I land on a GRUB4DOS screen, which is kind of like a commandprompt, only on startup. I've tried reinstalling multiple times, I've tried different distro's (Mint) in combination with different Windows (7, 8) versions and every single time I landed on this problem. I've tried boot-repair as well as updating Grub from the LiveUSB, but to no avail. Does anyone know where to go from here on out?

Here's the boot-repair link with info: [http://paste.ubuntu.com/6619473](http://paste.ubuntu.com/6619473)

---

### Post by oldfred on 2013-12-22
I do not know where you would get grub4dos. That is either wubi or EasyBCD usually.

I also do not know Elementary and what differences it may have.

But you have converted your system that was UEFI, gpt partitioned and Windows 8 to BIOS, MBR partitioned and Windows in BIOS boot mode.

Windows does not convert gpt partitioned drives back to MBR correctly when you install it in BIOS mode. It left the backup gpt partition table. MBR(msdos) has no backup, and Windows seems to ignore the gpt backup. Linux then sees both MBR and backup gpt and will not install correctly. But BootInfo report is not showing any gpt issues, so it now looks like a standard MBR install.

Does Windows boot ok now. You show a Windows boot loader in the MBR and standard two primary partitions for a BIOS Windows install.

If so use Boot-Repair or manually install grub to MBR.

What video card/chip do you have? What system is it?
Systems often boot thru grub, but then may not seem like it as video mode is wrong.

---

### Post by doncoyoteee on 2013-12-22
I have an NVIDIA card as well as an Intel graphics card; I've disabled the NVIDIA one in BIOS as I was told that it can cause problems with Linux. Windows is booting just fine now. 

As for the Grub4dos, I did use EasyBCD to get make an entry in the BIOS, but only after grub didn't show up upon first install of eOS. As far as I know Elementary Luna is based on Ubuntu 12.04.

To further explain what happens, here's a step-by-step:
1. I power on my computer
2. Lenovo screen pops up for about 2 seconds
3. I enter the EasyBCD interface and am given a choice to boot eOS or Win8
4. I select eOS
5. Grub4dos screen appears

As for the conversion from UEFI to BIOS, I was following up on something I had found on the internet in the hope that it would fix my problem; it did not. After doing this I had the problem that nor Windows 8 nor eOS would start, I fixed this by removing remnants of the gpt partition with a liveUSB of windows 8. 

As for bootrepair, I'm afraid that it does not work for me. Launching the tool goes well, but then when I instruct it to repair the boot, it does some things for a while and I get the message:
"Grub-pc purge cancelled"

---

### Post by oldfred on 2013-12-22
Part of the issue may be the dual video.

I do not know about EasyBCD, I think they have their own forums. But typically have to have grub installed to a partition or PBR, so grub4dos has a way to chainload. Having grub2 in a PBR is not recommended, but can be done. It is larger than old grub legacy to support all the new system configurations, so to fit into a PBR, it has to use blocklists or hard coded addresses. Updates may then move files to a new address and you then have to reinstall grub to PBR.

Intel usually works, but may need different boot parameters than nVidia which usually works with nomodeset. And dual video often then needs bumblebee.

Other Lenovo installs:
 Lenovo s440
[http://ubuntuforums.org/showthread.php?t=2189531](http://ubuntuforums.org/showthread.php?t=2189531)

Lenovo Yoga 11s (Intel i5/Intel HD 4000)
Needed this: acpi_backlight=vendor 
[http://ubuntuforums.org/showthread.php?t=2188199](http://ubuntuforums.org/showthread.php?t=2188199)
[http://ubuntuforums.org/showthread.php?t=1911972](http://ubuntuforums.org/showthread.php?t=1911972)&
Lenovo Community Bios Access
[http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2](http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2)
Lenovo Active Protection System&#8482; &#8211; for hard drive
 [SOLVED] Lenovo Y580 with working bumblebee on 12.10 - NVIDIA 660M
[http://ubuntuforums.org/showthread.php?t=2137318](http://ubuntuforums.org/showthread.php?t=2137318)
screen brightness was 0 during installation, use f12
Lenovo Z580 laptop
[http://ubuntuforums.org/showthread.php?t=2112271](http://ubuntuforums.org/showthread.php?t=2112271)
See post #29 on removing Battery to get it to reset &  boot Ubuntu.
[http://ubuntuforums.org/showthread.php?t=2117760](http://ubuntuforums.org/showthread.php?t=2117760)

---

