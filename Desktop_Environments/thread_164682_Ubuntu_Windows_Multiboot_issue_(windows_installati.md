---
title: "Ubuntu Windows Multiboot issue (windows installation after GRUB is in placed)"
date: 2006-04-23
forum: Desktop Environments
---

### Post by phoenixy on 2006-04-23
Hi,

I'm setting up a new PC and I am doing it in this manner: WinXP -> Ubuntu -> WinXP -> WinXP. The reason I'm doing this is that I want to make sure that I can reinstall Windows when GRUB is in charged.

My single disk is divided into the following partition (in order)
NTFS Primary
EXT2 (/boot) Primary
ReiserFS (/) Logical
SWAP Logical
unpartitioned free space

I plan to create 2 more NTFS partitions for the 2 extra Windows.

So far, I just finished installing Ubuntu. GRUB is dual booting the first Windows and Ubuntu. What I want to know is: what is the easiest way to install new Windows after GRUB had already taken charge?

If my assumption is correct, what I have to do is backup the MBR in linux, restore the XP MBR so that it thinks only XP exists; install 2 windows; restore GRUB MBR. Is this correct? If so, any good reference on how to backup the MBR?

Thanks!

---

### Post by red_shrike on 2006-04-23
Instzall Win first, and than Linux. If you do the opposite, than attempt installation of Linux but as soon as you get to the install menu choose install GRUB and ignore any error messages and simply continue. That worked for me.

---

### Post by jazzmuzik on 2006-04-23
I think you are complicating things. If you install Ubuntu and then Windows, Windows will overwrite the master boot record (MBR) and will seem to make it impossible to get into Linux, but Linux is still there. You just need to reinstall grub and it will fix the MBR.

I've been using Ubuntu for about a month now and I haven't actually tried this, but this is how I fixed the MBR in Fedora several times (and it worked):

boot up linux cd, type "rescue"
let the program find the linux installation on the hd
at the prompt type "chroot /media/sysimage"
type "grub-install /dev/hda"

However, let's see what others have to say on the matter.

---

### Post by phoenixy on 2006-04-23
Hi, 

Yes, I'm intentionally complicating the matter by installing windows after ubuntu., for the reason that I want to make sure I can reinstall windows

I understand that new windows will destroy GRUB's stuff in MBR and reinstalling GRUB will get it back. I am wondering if there is a way to do this without reinstalling GRUB?

---

### Post by lha on 2006-04-24
Hi phoenixy,

I'd say install grub on /boot partition and then let Windows take over mbr. (There are many reinstall/repair grub-howto's in these forums.) Then you can use partitioning tools to select which partition is bootable, Ubuntu's /boot or your primary ntfs. If you set /boot active, grub will be loaded and if you set that ntfs active, Windows is loaded like it would without Ubuntu. This saves you from the trouble of backing up mbr and restoring it every time you want to install Windows.

---

### Post by phoenixy on 2006-04-24
[QUOTE=lha]Hi phoenixy,

I'd say install grub on /boot partition and then let Windows take over mbr. (There are many reinstall/repair grub-howto's in these forums.) Then you can use partitioning tools to select which partition is bootable, Ubuntu's /boot or your primary ntfs. If you set /boot active, grub will be loaded and if you set that ntfs active, Windows is loaded like it would without Ubuntu. This saves you from the trouble of backing up mbr and restoring it every time you want to install Windows.[/QUOTE]

Hi,

Thanks for the advice. I think I pretty got it. Here is my thought

1. when Windows already existed on the first partition, Ubuntu by default install GRUB to MBR and the first partition is mark as active. I would had been better off if I mark /boot partition as active and install GRUB there. If I remember correctly the standard installaton CD didn't ask me about where GRUB should reside. Thus I should had pick not install GRUB and then manually do install it thru commandline. Then when I wish to install new Windows, all I have to do is toggle the bootable flag in fdisk to first partition, install, then toggle it back to /boot

2. Now that GRUB is in MBR, I guess I have to destroy it by running "fixmbr" from a Windows recovery console. Then I can install Windows and reinstall GRUB later (this time, to /boot).


I hope I got everything correct

---

### Post by phoenixy on 2006-04-24
1 minor question. If I choose to backup my mbr or boot sector information on other partition, dd can do the job right? Something like (for mbr) 

dd count=1 if=/dev/hda of=mbr. 

And vice versa for restore?

---

### Post by phoenixy on 2006-04-25
So I boot into ubuntu in rescue mode, pick my root partition, then mount hda2 to /boot. When I run the command grub-install /dev/hda2, everything seems fine. I checked the menu.lst file and it has not been overwriten. But for some reason, I am only getting a GRUB prompt when I reboot? GRUB is not reading the menu.lst file for some reason. I can use GRUB command line to boot Windows though.

Any quick way to make sure that GRUB reads the config file?

---

### Post by lha on 2006-04-25
[QUOTE=phoenixy]Hi,

Thanks for the advice. I think I pretty got it. Here is my thought

1. when Windows already existed on the first partition, Ubuntu by default install GRUB to MBR and the first partition is mark as active. I would had been better off if I mark /boot partition as active and install GRUB there. If I remember correctly the standard installaton CD didn't ask me about where GRUB should reside. Thus I should had pick not install GRUB and then manually do install it thru commandline. Then when I wish to install new Windows, all I have to do is toggle the bootable flag in fdisk to first partition, install, then toggle it back to /boot

2. Now that GRUB is in MBR, I guess I have to destroy it by running "fixmbr" from a Windows recovery console. Then I can install Windows and reinstall GRUB later (this time, to /boot).


I hope I got everything correct[/QUOTE]

1. Installer asks if it is ok to install grub to mbr. If you say no, you can enter where you would like to be.

2. Correct.

You can backup mbr with dd. I remember I used a bit different options. I'm sure Google will help you. :)

[QUOTE=phoenixy]So I boot into ubuntu in rescue mode, pick my root partition, then mount hda2 to /boot. When I run the command grub-install /dev/hda2, everything seems fine. I checked the menu.lst file and it has not been overwriten. But for some reason, I am only getting a GRUB prompt when I reboot? GRUB is not reading the menu.lst file for some reason. I can use GRUB command line to boot Windows though.

Any quick way to make sure that GRUB reads the config file?[/QUOTE]

Maybe that /boot partition complicates things too much for grub-install. Try to [install grub from installation cd]("http://ubuntuforums.org/showthread.php?t=76652").

---

### Post by phoenixy on 2006-04-25
Thank you for the support Iha:) 

Everything is working now. I decided to leave GRUB in the MBR and use dd to restore GRUB. It's really as simple as

save mbr (only need to do this once after GRUB is installed)
dd bs=446 count=1 if=/dev/hda of=/somewhere/mbr

restore mbr
dd bs=446 count=1 if=/somewhere/mbr of=/dev/hda

PS: 446 = 512 MBR - 64 partition table - 2 constant bytes

So, you are free to resize your partition table if you don't backup that last 64 bytes


A tricky problem that I ran into later on is that for whatever reason, WindowsXP installer decided that I am not allow to add more logical partitions to my extend](*,) ](*,) ](*,), which leave me with only one more windows on the last primary. I had to use the ubuntu CD's partitioner to creater 2 unused logical partitions. Then I boot into XP again, which says the partitions are unrecognizable and thus useless. But all is good since they are nevertheless logical partitions. Just delete them in XP installer and recreate these partitions.

Finally, I now have 3 XP and 1 linux running with the following installation order ( XP, linux, XP, XP ). I will tackle the network card and X issue when I have some free time

---

### Post by lha on 2006-04-25
[QUOTE=phoenixy]Thank you for the support Iha:) [/QUOTE]
You're welcome. Glad to hear it sorted out.

---

