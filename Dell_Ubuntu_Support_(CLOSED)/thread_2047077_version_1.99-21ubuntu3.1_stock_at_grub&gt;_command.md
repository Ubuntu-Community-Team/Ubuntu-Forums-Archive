---
title: "version 1.99-21ubuntu3.1 stock at grub&gt; command"
date: 2012-08-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Rotary Heart on 2012-08-24
Hi
I'm new to ubuntu, but I need it so I tried the wubi one to see if it works and it actually boot it the first time, but after a restart I got stock here:
I'm running it on Alienware M17X R1 windows 7 ultimate.

GNU GRUB version 1.99-21ubuntu3.1

Minimal BASH-like line editing is supported. For the first word, TAB
lists possible command completions. Anywhere else TAB
lists possible device or file completions.

grub>_

I writed ls and got
(memdisk) (loop0) (hd0) (hd0,msdos2) (hd0,msdos1)

Then: ls (hd0,msdos2) and got
Partition hd0,msdos2: Filesystem type ntfs, UUID 6C88C30688C2CDB0
Partition starr at 206848 - Total size 488181760 sectors

Then: ls (hd0,msdos1) and got
Partition hd0,msdos1: Filesystem type ntfs - Label "System Reserved",
UUID B44CC0494CC00856 - Partition start at 2048 - Total size 204800 sectors

I tried to get as much info as I can. I hope this is enough.
ThanksThanks

---

### Post by Rubi1200 on 2012-08-24
Hi and welcome to the forums :)

Please post the results of the boot info script.

There is a link at the bottom of my post with instructions.

Thanks.

---

### Post by Rotary Heart on 2012-08-24
So I have to re instal it? It says that I have to be inside ubuntu right? Or I didn't understand it.

---

### Post by Rubi1200 on 2012-08-24
Hi,

you will need to get hold of a LiveCD/USB and then boot the computer to be able to run the script.

It is a diagnostic tool to help find out what is gong on.

---

### Post by Rotary Heart on 2012-08-24
So how I can make a live cd or usb? Or get one? I don't have one

---

### Post by oldfred on 2012-08-24
You should have repairCD or USB for the current version of every system you have installed. Do you have the Windows repair CD?

If you have a friend or access to another computer with the same 32 or 64 bit Windows.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Wubi boots thru the Windows boot loader. It sounds like you have grub in the MBR. Running all the Windows repairs may update BCD and remove the wubi entry in the BCD or Windows boot menu.

---

### Post by Rotary Heart on 2012-08-24
Ok I uninstalled it and tried to install it making a bootable CD. Everything was going great, but when it was like at 75% and error message appear.

Unable to install GRUB in /dev/mapper
Executing 'grup-install/dev/mapper' failed
This is a Fatal error.

does this means that I can't install ubuntu on my computer?

Thanks

---

### Post by oldfred on 2012-08-25
/dev/mapper is usually RAID, or LVM or some other special device. The standard install does not include the drivers for those as that is normally a server. You can use alternative installer as that has the extra drivers.

If you have wubi, you should not be installing grub to a root device. Wubi uses the Windows boot loader. Or is this an error from wubi? I do not know a lot of details of wubi.

If you now have a bootable liveCD, download an run this, post link from BootInfo report:
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

### Post by Rotary Heart on 2012-08-25
> **oldfred said:**
> /dev/mapper is usually RAID, or LVM or some other special device. The standard install does not include the drivers for those as that is normally a server. You can use alternative installer as that has the extra drivers.

If you have wubi, you should not be installing grub to a root device. Wubi uses the Windows boot loader. Or is this an error from wubi? I do not know a lot of details of wubi.

If you now have a bootable liveCD, download an run this, post link from BootInfo report:
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

Well when I got it to boot it said that I need amd driver update, after installing it I restart it and now can't boot. Maybe it was a bad download?

Wil try what you said and will post results.

---

### Post by oldfred on 2012-08-25
Was the AMD a video driver?

From the Boot-Repair run the BootIno report and post link here.

---

### Post by Rotary Heart on 2012-08-25
> **oldfred said:**
> Was the AMD a video driver?

From the Boot-Repair run the BootIno report and post link here.

Yes a video driver. I think that I will have time to check that today.

---

### Post by Rotary Heart on 2012-09-04
Ok guys thanks for all your help, I found what my issue was. After doing a lot of tests and trying to do what you people said I found that I have a bad Hard Drive. Thanks to that HD I was having an issue that the ATI driver was installing in one HD and that was making the: "Driver not installed" issue.

But now I have one question more. I'm right now writing this with Ubuntu, wooohooo, but I have 2 drivers to install:

ATI/AMD proprietary FGLRX graphics driver (post-release update)
ATI/AMD proprietary FGLRX graphics driver

I allready activated the second one. Do I need to activate the first one too?

Thanks

---

### Post by oldfred on 2012-09-04
Bleeding edge or stable?

I have nVidia and turned on the post release version. That will update to the newest version but that may not have been fully tested with all the current applications so you then  are on your own.

---

