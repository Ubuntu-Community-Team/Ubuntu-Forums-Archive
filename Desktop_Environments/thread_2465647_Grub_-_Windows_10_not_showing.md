---
title: "Grub - Windows 10 not showing"
date: 2021-08-07
forum: Desktop Environments
---

### Post by Geoff_Lane on 2021-08-07
Toshiba Satellite laptop 64 bit AMD A8-7410 APU with AMD Radeon R5 Graphics × 4 
Ubuntu 20:04 LTS

Installed 20:04 from a live image yesterday alongside a rarely used Windows 10 installation.  All went fine and subsequently did a few tweaks to my new Ubuntu system.

Strangely on trying to boot today greeted with message - no boot medium found.  Using Live medium to investigate somehow my /boot menu is completely empty :frown:

After some attempted remedies decided reinstall quickest option.  All successful except Windows 10 does not show in the boot menu, os-prober doesn't find it but it is still there shown on gparted.  

[IMG]https://drive.google.com/file/d/1XfZzB5ugb0IYty-mTyzRESl8DURM5kCe/view?usp=sharing[/IMG][IMG]https://drive.google.com/file/d/1XfZzB5ugb0IYty-mTyzRESl8DURM5kCe/view?usp=sharing[/IMG]
[https://drive.google.com/file/d/1XfZzB5ugb0IYty-mTyzRESl8DURM5kCe/view?usp=sharing](https://drive.google.com/file/d/1XfZzB5ugb0IYty-mTyzRESl8DURM5kCe/view?usp=sharing)

I haven't touched the Windows partition so am puzzled what the issue is, any suggestions appreciated.

Geoff

---

### Post by alro7779 on 2021-08-07
Did you do a system update on Ubuntu? *sudo apt update* and then reboot. That fixes the issue most of the time to me.

---

### Post by oldfred on 2021-08-07
Are both systems installed in UEFI mode to gpt partitioned drive, or both in old BIOS/MBR mode?
And then is system set to boot in that mode. 

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Geoff_Lane on 2021-08-07
> **alro7779 said:**
> Did you do a system update on Ubuntu? *sudo apt update* and then reboot. That fixes the issue most of the time to me.

Yes, I did.  The /boot folder which I know loads from the EFI partition had no WINDOWS folder.

Geoff

---

### Post by Geoff_Lane on 2021-08-07
> **oldfred said:**
> Are both systems installed in UEFI mode to gpt partitioned drive, or both in old BIOS/MBR mode?
And then is system set to boot in that mode. 

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Solved it, maybe not the best way but working at the moment.  But there again, it was working yesterday :P

Had a backup of original Windows installation using Macrium Reflect.  Using a Macrium rescue boot USB you can browse backup images.  Copied the microsoft folder from the EFI partition to an attached USB storage.  Booted in to Ubuntu,  used root to copy the microsoft files into EFI folder.  update-grub and all working.

This post being made via Windows so it booted OK (till tomorrow) 8-)

Geoff

---

### Post by Geoff_Lane on 2021-08-08
> **oldfred said:**
> Are both systems installed in UEFI mode to gpt partitioned drive, or both in old BIOS/MBR mode?
And then is system set to boot in that mode. 

Lets see details, use ppa version with your live installer (2nd option) or any working install,  not Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Must admit the UEFI mode baffles me a wee bit and as I posted in a previous reply I sorted the issue by copying a microsoft folder the the efi partition, what baffles me is, I can manually boot from grub with just four lines;
```
set root='hd0,gpt5'
linux /boot/vmlinuz root=/dev/sda5
initrd /boot/initrd.img
boot

```

So what is the EFI folder for?

Geoff

---

### Post by oldfred on 2021-08-08
With UEFI, the system starts boot by reading the files in the ESP - efi system partition.
That has grub or shim version for Secure Boot and a tiny 3 line grub that is a configfile to load the full grub in your install.

With BIOS, the system starts boot by reading the MBR. The MBR is tiny, so grub also has a hidden file in the sectors just after the MBR, if MBR partitioned or in the bios_grub partition, if gpt partitioned to search for grub.cfg. 

If booting from an old grub, where you updated or reinstalled & grub has old UUID, then you get the grub command line. Or some other issues like using old BIOS grub in MBR but have UEFI install.
When you manually type in the partition and load kernel you are not using  the original setting & not finding a grub.cfg to load the menu. You had enough of grub installed to give grub command line & let you manually boot.

---

### Post by Geoff_Lane on 2021-08-08
Thanks Fred,  that has clarified the mud a bit more, still a bit murky but I do seem to be able to overcome some boot issues, maybe more by luck than knowing exactly what I am doing.  8-)

Geoff

---

### Post by yancek on 2021-08-08
>   All went fine and subsequently did a few tweaks to my new Ubuntu system.
 

When you are doing 'tweaks', you should always make note of what changes you make so you can post them so that people who are more familiar may be able to help.  The tweaks you made may have had an effect on your booting problem but since you haven't posted them, there is no way to tell.

>  my /boot menu is completely empty 

What boot menu?  Are you referring to the grub.cfg file in the /boot/grub directory or no boot menu showing on boot?

> After some attempted remedies  

Again, you should make note of any 'remedies' you tried so you can post them.  If you tried solution on some web site, you should post a link to the site.

>  Windows 10 does not show in the boot men 

The 2 most common reasons for this are leaving windows hibernated which means the windows partition will not be mounted and no entry for windows will show in the grub.cfg menu.  The other major reason is installing one OS in Legacy/CSM mode and the other in EFI mode.

The most helpful source of information when using Ubuntu i the boot repair software which was suggested by Oldfred in post 3.  That usually gives enough information to help restore booting.  Using the Creat BootInfo Summary option is what you should use with boot repair.

>  The /boot folder which I know loads from the EFI partition had no WINDOWS folder.
  

I'm not sure what you are referring to here.  The boot folder on your Ubuntu system will not have any WINDOWS folder.  The EFI partition will have a Microsoft folder which contains a Boot folder and in this folder you will (or should) have an bootmgfw.efi file which is reqired to boot windows EFI.

>   Copied the microsoft folder from the EFI partition  

As pointed out above, there should have been a Microsoft foler on your hard drive EFI partition.  If you had it on your backup of the OS that would indicate that the Microsoft folder was originally on the windows system and somehow was deleted.

>  Must admit the UEFI mode baffles me  

Had the same problem as I had familiarized myself with Grub2 prior to EFI so a lot of reading needed to understand it .  The 2 major changes in EFI which make it better are the ability to boot directly from the EFI menu in the BIOS firmware boot options and the fact that installing a new OS will not have the boot code overwritten in the MBR as the MBR is not used for booting but rather your EFI partition is.  On Legacy installs, most Linux OS's will have a default selection to overwrite the current MBR with the new OS's boot code in the MBR.  Generally, with most Linux system, you are given an option to install to the MBR or a partition.  Most users, from what I've seen, do not notice this and overwrite the boot code in the MBR

Since an EFI install will create a separate folder for its EFI boot files, this problem is eliminated.

The EFI folder contains the files necessary to boot and if the correct files are in place, an entry will be created and you will have a menuentry created in the grub.cfg file so you will not need to manually enter the lines you have posted in post # 5 above.  It's handy to have that entry written down somplace if your grub.cfg file gets messed up.  The entry below will boot a windows from the grub prompt, as long as the necessary files are in place on theEFI partition.  The set root line will need to point to the EFI partition and I'm sure you are aware that you hit the Enter key after each line.

>   insmod part_gpt
insmod chain
set root=(hd0,gpt1)
chainloader /EFI/Microsoft/Boot/bootmgfw.efi
boot
.

---

### Post by Geoff_Lane on 2021-08-09
Yancek,

Thank you for in depth reply, I think one mistaken word in my post may have caused confusion.  I said using a Live Image I checked the non booting system on my hard drive found my /boot menu was empty, I meant the **/boot directory **was empty.  The rest of the file system was intact but as it was a very recent reinstall I decided the easiest option would be to reinstall again.

Re your comment about keeping note of tweaks, when you don't expect things to go wrong one doesn't normally keep note of various tweaks made butt from memory it was merely an apt update && upgrade, change background wallpaper, install net-tools etc.

Certainly nothing major.

I did have that chainloader option showing but as said, my /boot folder was completely empty.  I know that gets mounted with the EFI partition and I didn't check the /etc/fstab file but all is working fine now.

I have seen the option where to install GRUB and must admit I've always gone for MBR - are you suggesting the partition would be preferable?  Recall doing that with GRUB-Legacy but not with latest grub.

Must admit I have manual entries in /etc/grub.d/40_custom to boot some external USB distros (if they are plugged in) and my main system too.

Geoff

---

### Post by yancek on 2021-08-09
>  when you don't expect things to go wrong one doesn't normally keep note of various tweaks 

It's often when we don't expect things to go wrong that they do and it's better to have it and not need it to need it and not have it.

>  have seen the option where to install GRUB and must admit I've always  gone for MBR - are you suggesting the partition would be preferable?  

The standard on MBR installs was to install to /dev/sda which would put Grub boot code in the MBR and most of the Grub files on the system partition.  You can select a partition to install Grub to if you have another Grub installed in the MBR on a Legacy install.  For an EFI install, the /dev/sda choice will install boot code to the EFI partition where it needs to be.

---

### Post by Geoff_Lane on 2021-08-10
Thanks Yancek.

Geoff

---

