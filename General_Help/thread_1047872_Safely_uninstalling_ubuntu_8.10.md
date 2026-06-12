---
title: "Safely uninstalling ubuntu 8.10"
date: 2009-01-22
forum: General Help
---

### Post by huiwiz on 2009-01-22
Hello, I'm new to anything linux...and I don't really know what I'm doing...
I was thinking I'd try something a little different, so I decided to download and try Ubuntu 8.10.
To avoid damaging my current OS and files (Windows XP), I thought I'd try to install Ubuntu on a separate. Anyways, Ubuntu doesn't run very well on my computer because of its Intel graphics chip, and I much prefer my old Windows.
So I looked through the Linux files for an uninstaller, but I found nothing in either the File System, or the CD.
So using the Live Cd, I just went ahead and deleted the Linux partition, and reclaimed the space for my Windows partition.

When I rebooted my computer, the OS selection screen came up, but it gave me an error ("error 22", I think it was). It wouldn't let me choose to boot my Windows XP...it just gave me a blank screen. I couldn't do anything but restart my computer.
The only way I could access my Windows XP operating system was to reinstall Ubuntu, which is what I wanted to delete in the first place.


How can I safely delete my Ubuntu 8.10 partition without damaging my Windows Partition? And how can I make Windows XP my default OS again?

---

### Post by cdtech on 2009-01-22
After you reclaim the space use the Windows install CD and repair the MBR. That will get you back into Windows. Removing or formating the Linux partitions do not remove the GRUB boot loader, which was installed during installation. Just repair the MBR using the XP install disc........

---

### Post by adult swim on 2009-01-22
you need to do what you did earlier, delete the linux partition and reclaim it to windows.  then you need to boot your windows xp cd and go to the recovery console.  from there you need to enter in ```
fixboot

fixmbr

exit (if exit doesnt get you out of there, try quit)
``` then reboot and windows should fire up like normal.

---

### Post by kuriozux on 2009-01-22
> **cdtech said:**
> After you reclaim the space use the Windows install CD and repair the MBR. That will get you back into Windows. Removing or formating the Linux partitions do not remove the GRUB boot loader, which was installed during installation. Just repair the MBR using the XP install disc........

hi, is there a way to re-install windows after removing partitions?

I removed all partitions and now all i have is the Grub loading and cannot boot from CD.

---

### Post by Paul Miller on 2009-01-22
.

---

### Post by cdtech on 2009-01-23
> **kuriozux said:**
> hi, is there a way to re-install windows after removing partitions?

I removed all partitions and now all i have is the Grub loading and cannot boot from CD.

How did you remove the partitions? Did you remove Windows as well? You'll have to set the BIOS to boot from the CDrom drive first...

---

### Post by huiwiz on 2009-01-23
Thank you. I now know how to fix the MBR....but now I have a much bigger problem...

I don't know the administrator password for my computer. When I press R in the Windows XP setup menu, it tells me to input the Administrator's password. I don't have a password on my computer though. So I left it blank, and it said that that was the wrong password. I put in my old password, but it still said it was wrong. So I rebooted XP and put a password on. I tried the recovery console again, but it still said that the password was incorrect.
My XP account name is Administrator, but I don't have a password set on it. How can I fix my MBR if I don't have the password for my own computer? Is there a way to figure it out? Or can I do something else?

---

### Post by cdtech on 2009-01-23
Try "administrator" for the password. I can't remember the default for XP, but try that.......

---

### Post by huiwiz on 2009-01-25
I tried a lot of things as the password. I left it blank (which is the default for XP, apparently), and I even used a Password Hacking Tool to figure out all of the passwords on my XP installation! But nothing works!

---

