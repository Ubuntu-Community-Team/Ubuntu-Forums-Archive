---
title: "black screen on startup"
date: 2009-05-07
forum: General Help
---

### Post by david kirkpatrick on 2009-05-07
when i start up every thing goes alright to start up screen (ubuntu and bar)then it goes black, pressed crtl alt f1 get me to a screen which show the following details [   7.254705] powernow-k8: bios error - no PSB or ACPI_PSS objects
loading please wait...
1940 records in
1940 records out
knit: name_to_dev_t(/dev/disk/by-uuid/26af7b12-fd46-4483-83d4-3f6a59e2b7a5) = dev(8,37)
knit: trying to resume from /dev/disk/by-uuid/26af7b12-fd46-4483-83d4-3f6a53e2b7a5
knit: no resume image, doing normal boot
mount: mounting /dev/disk/by-uuid/7dbdd4c7-3556-46b5-9da8-426e97f1cac7 on /root failed; invalid argument
mount: mounting /dev on /root/dev failed: no such file or directory
mount: mounting /sys on /root/sys failed: no such file or directory
mount: mounting /proc on  on /root/proc failed: no such file or directory
target filesystem doesn't have /sbin/init.
no init found. try passing init- bootarg.

BusyBox v1.10.02 (Ubuntu 1:1.20.2-2ubuntu7) built-in shell (ash)
Enter "help" for a list of built_in  commands.
(initramfs) flashing cursor here

I have read other messages but I do not think that they are similar to mine as my system was working last night (6th May), though the last few times that I have sgutdown it has been bleeping at me on shutdown, but no messages were shown on screen just the bleeps 3 of them if that suggests any thing to any one, I was having problems before this in that grub was loading the wrong kernel (8.04 not 9.04) so that when I tried to install mt nvidia graphic card driver they were not bring installed solved that by changing the drive  detail in menu.lst then had no problem installing the driver even got compiz-fusion working (bit more complicated than I would like as there is no user guide for it, is there? I down loaded a Jaunty disk from Ubuntu via my other computer a G4 Mac burned it verified it no problems, will not boot from it so cannot check if the computer will run from a live disk.
the computer that I use is a home build so no make or model.
The mother board is a GIGA-BYTE K8 triton, GA-K8NTF-9, nForce-4x chipset, 
display card is a PNY GF8400GS NVIDIA graphic card,
was running a ATI radon x550, but had a problem with it I think I set my display too to large a display setting so replaced with the Nvidia card My monitor is a Samsung SyncMaster 913b,
1 SATA drive 300GB split in half, 3 ATA drive 1 in a removable caddy, 2 optical drves both DVD  only one is a writer a floppy and a ZIP drive, 2 external usb drives which I have to manually mount every time I restart, also one is a NTFS which I am told I cannot mount because i do  not have the right permissions, and that I should also get the module that reads/ write NTFS drive recompiled added to the kernel?? I have to use forgotten the programs name, the one that set the hard drive setting, and mount them from there also it seems to have lost also to put on to the desktop the boot i.e. the one that haas the file system on it also the split SATA hard drives have to select then via the menu as it shows them as removable?. But the main problem is just not getting beyond the black screen. Any ideas folks, I still regard my self as a newbie even though I have been using Ubuntu since breezy, the other OS I use is OS X on my G4, the only time I use  Windows is at work these day even my laptop run Ubuntu. there is one oddit that I have come a cross, it is when I try and use my Phillips web cam, I get a picture but it is A) wrong colour,B) upside down, so have given up trying to use it. sorry that this message is so long. Hope that some one can help me with the main problem the rest can wait till i can access my desktop again, Hope I have better luck with this message as I have never got a reply from any of the other that I have posted to any forum

---

### Post by david kirkpatrick on 2009-05-09
fixed it but do not ask me how, I managed to boot from a old live disk copy of 7.04 I also figured out how to get in as root to make changes, just like when you add a new user to the system but make the pass word upper-case, log out then log back in using the root or add your self as normal.

---

### Post by david kirkpatrick on 2009-05-09
fixed it but do not ask me how, I managed to boot from a old live disk copy of 7.04 I also figured out how to get in as root to make changes, just like when you add a new user to the system but make the pass word upper-case, log out then log back in using the root or add your self as normal.
Thing is now Amarok has broke it tells me my sound system is not working, if it is not one thing it is another, think maybe them may have made a few too many changes to 9.04, lost the notifier for updates as well.

---

