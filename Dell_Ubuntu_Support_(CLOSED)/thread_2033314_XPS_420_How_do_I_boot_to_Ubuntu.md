---
title: "XPS 420: How do I boot to Ubuntu?"
date: 2012-07-25
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Soukuw on 2012-07-25
This might be a easy as hell thing to fix with something stupid but I can't figure it out:
I installed Ubuntu it finished I rebooted but it goes right to Win7 rather then giving me a choice between the two how do I fix this?

I've installed Ubuntu a bunch before (Different computers) and it's always given me a choice. Also I can't seem to find anything that implies Ubuntu has been installed on the System besides the fact that when I put the install disk in and run it it says it's installed and my choices are to reinstall it, if I try to reinstall it it will say the partition is full.

---

### Post by oldfred on 2012-07-25
Welcome to the forums.

We need to see the details, run the BootInfo report and post the link from this:

Boot Repair -Also handles LVM, GPT and separate /boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration.

---

### Post by Soukuw on 2012-07-26
Alright so I attempted to do this the screen freaked out tried to just repair it didn't work and had a host of errors and weird windows.

Is there an easy way to completely wipe Ubuntu off the computer without hurting Windows 7 so I can do a fresh install?

---

### Post by oldfred on 2012-07-26
If you use Something Else or manual install, you can just reinstall using the same / (root), choose it and format. It will find swap automatically. If you have a separate /home with data you want to save, you mount it but DO NOT format it.

You can also change partitions during a reinstall with manual install or use gparted from liveCD.

Is this a new system with UEFI and Window in UEFI mode? If so, you need to boot the Ubuntu installer in UEFI/efi mode not BIOS mode.

You may still have video issues, which may need boot parameters to work.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Soukuw on 2012-07-30
After deleting all of my partition in Windows and reinstalling it worked perfectly.

---

