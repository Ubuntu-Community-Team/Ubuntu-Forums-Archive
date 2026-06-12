---
title: "Grub Does Not Recognize USB Flash Stick During Boot"
date: 2016-06-01
forum: Desktop Environments
---

### Post by ping-wu on 2016-06-01
Computer: HP Envy Intel I7, SSD, Ubuntu 14.04 LTS, EFI in (hd0,gpt1), system installed in (hd0, gpt2).  

USB stick: GPT-partitioned, EFI in (hd1,gpt1, with grub-boot flag) and the same Ubuntu 14.04 LTS system installed in (hd1,gpt2).

I did an update-grub such that I can see the option of booting into the USB stick during grub boot.  However, after I selected this boot-to-(hd1,gpt2) option, an error message was shown, basically saying that (hd1,gpt2) was not found. Initially I used the EFI flag for the (hd1,gpt1) partition, same result.

I went into the grub prompt and entered an "ls" command.  The output only shows the partitions on the (hd0) drive, no (hd1) partition was recognized.

After I booted into (hd0, gpt2), I can see all the partitions on the flash stick (hd1).  However, again as stated above, the flash stick (hd1) was not recognized during grub boot.

---

### Post by oldfred on 2016-06-01
Not sure what type of entry grub created. I would think it would be able to directly boot an install on your flash drive.

But external drives with UEFI only boot from /EFI/Boot/bootx64.efi. Both Windows & Ubuntu use that name, but of course different files.
Grub does not like a second ESP on sdb. I get some sort of invalid nested partition error.

You can just copy your /EFI/ubuntu from the ESP on sda to the esp on sdb. Then copy again from /EFI/ubuntu to /EFI/Boot and then rename shimx64.efi to bootx64.efi. The copy of grub/shim you copy and rename internally is hard coded to find files in /EFI/ubuntu, so you need that. 

I do something similar on my internal drives.  I copy grubx64.efi to /EFI/Boot and rename to bootx64.efi, so I have another way to boot from UEFI.

Then you can directly boot flash drive from UEFI or one time boot key like f10 or f12.

---

### Post by sudodus on 2016-06-02
Many HP computers do not want to boot *via USB* directly from GPT partitioned drives at all and not via grub in MSDOS partitioned drives unless there is a boot flag.

It is possible to boot originally from another drive and chainload also GPT partitioned drives and drives without the boot flag.

See these links:

[Pendrive ability to boot]("http://ubuntuforums.org/showthread.php?t=2196858&p=12907221#post12907221")

[mkusb/persistent#Partitions](https://help.ubuntu.com/community/mkusb/persistent#Partitions)

[Installation/FromUSBStick#Chainloading](https://help.ubuntu.com/community/Installation/FromUSBStick#Chainloading)

---

### Post by yoshii on 2016-06-02
I also have an HP Envy, and it only boots via USB drive if I first press ESC (several times until it shows) to get the startup menu.  Then, the menu says to press F9 to select the boot device.  From there, I can choose the USB drive listed by it's hardware name and boot from it as long as the USB drive has a bootable OS on it and has it's boot flag set to on.  You can use gParted to set the boot flag.  I hope this helps.

---

### Post by ping-wu on 2016-06-03
> **yoshi2 said:**
> I also have an HP Envy, and it only boots via USB drive if I first press ESC (several times until it shows) to get the startup menu.  Then, the menu says to press F9 to select the boot device.  From there, I can choose the USB drive listed by it's hardware name and boot from it as long as the USB drive has a bootable OS on it and has it's boot flag set to on.  You can use gParted to set the boot flag.  I hope this helps.

Looks like this is the only way to boot from a USB drive on the HP Envy (UEFI) machine.  

In order to boot from the USB drive, I also had to follow the steps described in OldFred's reply above:
   [COLOR=#000000] 
[/COLOR]> **oldfred said:**
>  copy your /EFI/ubuntu from the ESP on sda to the esp on sdb. Then copy again from /EFI/ubuntu to /EFI/Boot and then rename shimx64.efi to bootx64.efi. 

I am now able to boot from this installed Ubuntu (14.04 LTS) USB stick on an HP Envy notebook (also Ubuntu 14.04 LTS), as well as on an Acer E17 notebook (Windows 10).

---

### Post by sudodus on 2016-06-03
Congratulations and thanks for sharing your solution, *ping-wu* :-)

-o-

You have a newer HP computer than we have in my family. If you are interested and have the time, it would be valuable, if you can test an 'UEFI-and-BIOS' installed system in 'another pendrive with at least 8 GB': The test would overwrite the existing system, so I would recommend, that you use another pendrive, not the one where you have your own system now. See the following link,

[Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

I'm thinking of the compressed file

[dd_text_16.04-UEFI-n-BIOS_2016-05-27_4-pendrive-7.8GB.img.xz](http://phillw.net/isos/linux-tools/uefi-n-bios/dd_text_16.04-UEFI-n-BIOS_2016-05-27_4-pendrive-7.8GB.img.xz)

or if you have Intel graphics

[]dd_text_16.04-UEFI-n-BIOS_2016-05-27_intel-4-pendrive-7.8GB.img.xz](http://phillw.net/isos/linux-tools/uefi-n-bios/dd_text_16.04-UEFI-n-BIOS_2016-05-27_intel-4-pendrive-7.8GB.img.xz)

---

### Post by ping-wu on 2016-06-04
> **sudodus said:**
> Congratulations and thanks for sharing your solution, *ping-wu* :-)

-o-

You have a newer HP computer than we have in my family. If you are interested and have the time, it would be valuable, if you can test an 'UEFI-and-BIOS' installed system in 'another pendrive with at least 8 GB': The test would overwrite the existing system, so I would recommend, that you use another pendrive, not the one where you have your own system now. See the following link,

[Installation/UEFI-and-BIOS]("https://help.ubuntu.com/community/Installation/UEFI-and-BIOS")

I'm thinking of the compressed file

[dd_text_16.04-UEFI-n-BIOS_2016-05-27_4-pendrive-7.8GB.img.xz]("http://phillw.net/isos/linux-tools/uefi-n-bios/dd_text_16.04-UEFI-n-BIOS_2016-05-27_4-pendrive-7.8GB.img.xz")

or if you have Intel graphics


[]dd_text_16.04-UEFI-n-BIOS_2016-05-27_intel-4-pendrive-7.8GB.img.xz]("http://phillw.net/isos/linux-tools/uefi-n-bios/dd_text_16.04-UEFI-n-BIOS_2016-05-27_intel-4-pendrive-7.8GB.img.xz")


I have been able to plug this USB stick into several different brands/models of UEFI-based laptops and "externally" boot Ubuntu from there.  To me at least, this was a very exciting development.

Since this is an installed system, I can apt-get extra packages and update/upgrade the system without any problem. Performance-wise, there is no difference from an internal hard drive, except that my external USB stick (USB 3.0) is definitely faster than the internal HDD.

I still have not figured out how to boot this USB stick from an MBR-based machine.  However, since most of our MBR-based machines either do not have USB 3.0 (only USB 2.0), or have only early versions of USB 3.0 firmware, it's probably not a good idea to run an installed USB on those relatively old machines.

We have spent a lot of time developing an SOP of making customized (compressed) read-only Ubuntu iso images.  Our experience seems to indicate that, for those compressed read-only iso images, there is not a lot of performance difference between USB 2.0 and 3.0 sticks.

---

### Post by sudodus on 2016-06-04
> **ping-wu said:**
> I have been able to plug this USB stick into several different brands/models of UEFI-based laptops and "externally" boot Ubuntu from there.  To me at least, this was a very exciting development.

Since this is an installed system, I can apt-get extra packages and update/upgrade the system without any problem. Performance-wise, there is no difference from an internal hard drive, except that my external USB stick (USB 3.0) is definitely faster than the internal HDD.

Sounds great :-)
> 
I still have not figured out how to boot this USB stick from an MBR-based machine.  However, since most of our MBR-based machines either do not have USB 3.0 (only USB 2.0), or have only early versions of USB 3.0 firmware, it's probably not a good idea to run an installed USB on those relatively old machines.

You can install grub-pc (temporarily), create a small partition with the bios_grub flag and without any file system. Then you can install grub for BIOS mode. See the details at this link [Installation/UEFI-and-BIOS/stable-alternative](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative)
> 
We have spent a lot of time developing an SOP of making customized (compressed) read-only Ubuntu iso images.  Our experience seems to indicate that, for those compressed read-only iso images, there is not a lot of performance difference between USB 2.0 and 3.0 sticks.

Interesting! Are these systems also 'installed systems', 'live systems' or 'persistent live systems'?

---

### Post by ping-wu on 2016-06-04
> **sudodus said:**
> Sounds great :-)

You can install grub-pc (temporarily), create a small partition with the bios_grub flag and without any file system. Then you can install grub for BIOS mode. See the details at this link [Installation/UEFI-and-BIOS/stable-alternative]("https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative")

  

Thanks for the info.  I thought the MBR-partitioned drive does not need a bios_grub partition?  Can I create a new bios_grub partition anywhere in the USB stick? On a logical partition?

(I need to mention that, although I plan to use this "installed" USB stick almost exclusively on new computers with esp, it was MBR partitioned.)


 > **sudodus said:**
> Interesting! Are these systems also 'installed systems', 'live systems' or 'persistent live systems'?

I probably did not describe it clearly enough.  Because of the importance of having a "customized" bootable USB in this project of ours, we have two systems: "installed system" and "live system".  The live system has a multi-boot configuration to allow an advanced user to boot into persistent mode, as well as to allow for multiple locales (for now, only en_US.UTF-8 and zh_CN.UTF-8).  The persistent mode is often too slow for daily use (and can quickly out-grow allocated space).  We use the persistent mode to make modifications to the live system, then incorporate the changes into a new live system.

---

### Post by sudodus on 2016-06-04
> **ping-wu said:**
> Thanks for the info.  I thought the MBR-partitioned drive does not need a bios_grub partition?  Can I create a new bios_grub partition anywhere in the USB stick? On a logical partition?

(I need to mention that, although I plan to use this "installed" USB stick almost exclusively on new computers with esp, it was MBR partitioned.)

I see. You are right, a bios_grub partition is only for GPT. In an MSDOS partitioned drive (MBR), the extras of grub are stored in the first MiB before the first partition without any particular partition.
> 
I probably did not describe it clearly enough.  Because of the importance of having a "customized" bootable USB in this project of ours, we have two systems: "installed system" and "live system".  The live system has a multi-boot configuration to allow an advanced user to boot into persistent mode, as well as to allow for multiple locales (for now, only en_US.UTF-8 and zh_CN.UTF-8).  The persistent mode is often too slow for daily use (and can quickly out-grow allocated space).  We use the persistent mode to make modifications to the live system, then incorporate the changes into a new live system.

English and Chinese :-) (I am Swedish)

---

### Post by ping-wu on 2016-06-06
> **ping-wu said:**
> I still have not figured out how to boot this USB stick from an MBR-based machine. 

I am still unable to boot the installed USB from both UEFI- and MBR-based machines.  Any suggestion will be appreciated.  

As Rod Smith described:

 [http://askubuntu.com/questions/742225/how-to-make-uefi-ubuntu-bootable-from-mbr-drive](http://askubuntu.com/questions/742225/how-to-make-uefi-ubuntu-bootable-from-mbr-drive)

I probably need to try a non-GRUB option for the installed USB.  (I am using the syslinux option for our "customized" live USB, which can boot from both types of machines.)

---

### Post by sudodus on 2016-06-06
Grub works for me, as described in post #3 and post #6.

You have to install both grub-pc and grub-efi, which is described with some details in the links from those posts. There might be problems that I am not aware of with HP Envy, which is newer than the HPs in my family. I have not tried in that HP model.

I think it helps if you do these tasks (installing grub-pc and grub-efi, particularly grub-efi) in a computer without an internal drive, so that the target USB drive can be /dev/sda or at least the only drive except the live drive from which you are installing.

---

