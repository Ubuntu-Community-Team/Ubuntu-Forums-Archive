---
title: "Fixing Windows through linux."
date: 2009-03-31
forum: General Help
---

### Post by ucal on 2009-03-31
Hey guys.  I don't know if this is appropriate for this forum, but this is the best place I can turn to right now.  For some unknown reason, my windows partition has completely stopped working.  Linux still works (imagine that:D), but I can't access my partition through linux anymore.  I had it so both partitions that windows used would mount on start, but the partitions that has all the data won't mount anymore.  This makes me 99% certain that the error lies in the partition.  When I try and force the partition to start it returns to me the error that the harddisk is in use.  Any ideas?

---

### Post by TyrantWave on 2009-03-31
Open GParted, and check whether the windows partition is mounted.

If it is, then unmount it, and try to repair partition (GParted is very good at this). If it isn't mounted, see if you can mount it through GParted to access your data.

---

### Post by bgerlich on 2009-03-31
Try to mount it with the "sudo mount -a" command, afterwards type in "dmesg | tail -n 30" and post the result - it will tell us why the disk isn't mounting.

---

### Post by coffeecat on 2009-03-31
> **ucal said:**
> When I try and force the partition to start it returns to me the error that the harddisk is in use.  Any ideas?

That probably means that the filesystem journal is corrupted because of an unclean shutdown. If you can't boot into Windows, it probably means the Windows C: partition is similarly affected. Did you have an unclean shutdown last time you used Windows, or power failure, or something like that?

Windows NTFS partitions are best repaired using Windows. Can you boot up in safe mode? After you select Windows from the grub menu, press F8. If you get the Advanced Options Menu, select safe mode and see if it will boot. If it does, you might be able to repair both C: and the data partition.

Failing that, if you can get hold of a Windows install CD (not an OEM manufacturer's image disc), boot up with that, go into the repair console and run chkdsk.

I'm assuming you're using Windows XP and NTFS partitions. If they are FAT32 partitions, they are less likely to be repairable, but still worth trying.

---

### Post by ucal on 2009-03-31
```
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda3': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda3 /media/sda3 -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda3 /media/sda3 ntfs-3g force 0 0
```

I don't know how to repair it.

---

### Post by bgerlich on 2009-03-31
```
sudo mount -t ntfs-3g /dev/sda3 /media/sda3 -o force,ro
```

This will mount you partition read only allowing you to copy data without (further) endangering data integrity.

---

### Post by ucal on 2009-03-31
> **coffeecat said:**
> That probably means that the filesystem journal is corrupted because of an unclean shutdown. If you can't boot into Windows, it probably means the Windows C: partition is similarly affected. Did you have an unclean shutdown last time you used Windows, or power failure, or something like that?

Windows NTFS partitions are best repaired using Windows. Can you boot up in safe mode? After you select Windows from the grub menu, press F8. If you get the Advanced Options Menu, select safe mode and see if it will boot. If it does, you might be able to repair both C: and the data partition.

Failing that, if you can get hold of a Windows install CD (not an OEM manufacturer's image disc), boot up with that, go into the repair console and run chkdsk.

I'm assuming you're using Windows XP and NTFS partitions. If they are FAT32 partitions, they are less likely to be repairable, but still worth trying.

I just tried safe mode.  That's a no go.  Crashes to the "Windows failed to start up" screen.  I most likely did have an unclean shut down last time.  For some reason my computer turns itself off in the middle of the night (don't know why) if I'm not using it.  

I'll see if I can get a hold of a vista cd.  I think someone on my floor has one.

> Re: Fixing Windows through linux.
Code:

sudo mount -t ntfs-3g /dev/sda3 /media/sda3 -o force,ro

This will mount you partition read only allowing you to copy data without (further) endangering data integrity. 

Thank you.  Failing being able to solve the problem, this will be of great help.

---

### Post by coffeecat on 2009-03-31
> **ucal said:**
> > Re: Fixing Windows through linux.
Code:

sudo mount -t ntfs-3g /dev/sda3 /media/sda3 -o force,ro

This will mount you partition read only allowing you to copy data without (further) endangering data integrity.
Thank you.  Failing being able to solve the problem, this will be of great help.If you haven't installed it already, you'll need the ntfsprogs package in Ubuntu for this.

---

### Post by ucal on 2009-03-31
I managed to find an install cd.  It's for a 64bit system though.  How do I get chkdisc running from boot?

---

### Post by coffeecat on 2009-03-31
I have no experience of Vista, but with XP, you boot up from the CD, and when the Welcome to Setup screen comes up you press 'R' to give you a recovery console. You follow the short dialogue that follows and you end up with an old-style DOS prompt from which you can issue old-style DOS commands. To check your C: partition, you would use the command 'chkdsk C: /f /r'. (chkdsk, NOT chkdsic.) 

If the Vista is different in how to get to a recovery console, I'm afraid you'll have to do some googling, but [here's something to get you going - chkdsk in Vista]("http://searchenterprisedesktop.techtarget.com/generic/0,295582,sid192_gci1276029,00.html").

---

### Post by ucal on 2009-03-31
I found out how to run chkdsk, and i've tried to, but My windows installation doesn't appear in this menu, so I don't think that it will help at all.  

[http://helpdesk.wisc.edu/images/group1/6565/03_OS_select.jpg](http://helpdesk.wisc.edu/images/group1/6565/03_OS_select.jpg)

I guess my partition is totally borked.

---

### Post by coffeecat on 2009-04-01
Is there any way of getting to a command prompt with the Vista CD? That image shows some sort of GUI. It's just possible the command prompt may work where the GUI utility doesn't. Or, could you get hold of a Windows XP CD? Then you can definitely get into a repair console (see my earlier post) to run chkdsk.

Don't forget that in Ubuntu you still have this for the data partition:

```
sudo mount -t ntfs-3g /dev/sda3 /media/sda3 -o force,ro
```You'll need to install ntfsprogs for this.

Last thing, [the System Rescue CD]("http://www.sysresccd.org/Main_Page") might just help. It's probably going to have no more than what you can install in Ubuntu, but it's worth looking at.

**Edit:** no, not last thing. Just had another thought. Have a look for testdisk in Synaptic. It includes the app photorec. It has tools for partition recovery and photorec can be used to recover files (not just image files) from borked partitions. I have no experience of this, but I have read good reports of it. I've also noticed posts where people have posted lnks to howtos for using testdisk. I don't have any bookmarked, but a search of the forum should throw something up for you.

---

