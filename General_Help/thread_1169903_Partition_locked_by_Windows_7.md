---
title: "Partition locked by Windows 7"
date: 2009-05-25
forum: General Help
---

### Post by cablejimmy on 2009-05-25
I've got the release client of Windows 7 installed and Ubuntu Jaunty installed, each on separate partitions. I have a third partition on my hard drive which I want to use to store all my documents, but I can only access it in Windows.

I made it in gParted out of free space I had after installation of the two OS's. Then, I booted up Windows, and everything was working fine, but I think Windows locked the 3rd partition up when I used it, because now whenever I try to access it in Ubuntu, it says The enclosing drive for the volume is locked.

How do I stop windows from locking my partition?

---

### Post by coffeecat on 2009-05-25
Is the locked partition an NTFS one? If so, that's a new one on me. Curious. So far Windows 7 hasn't done this to me, but time will tell I suppose. <sigh>.

Anyway, I couldn't find anything in W7 about locking partitions, but I wonder if this is something to do with Windows permissions. NTFS doesn't support Linux/Unix permissions and Windows knows nothing about them anyway, but there's a whole set of Windows permissions. Perhaps Windows 7 has set a flag which Ubuntu is interpreting as locked. I'm just theorising here - I don't know.

Whatever - try this: in Windows 7 go to Computer, right-click on the 3rd partition and select properties. Click on the Security tab and have a look at the permissions. With my NTFS shared data partition, I'm seeing: Group or user names: Everyone. And, under Permissions for everyone: everything ticked under the allow column except Special Permissions. Last time I checked, everything was fine, so I'm now going to write something to that partition from Windows 7 and then reboot into Jaunty. :?

---

### Post by coffeecat on 2009-05-25
No, everything's fine on my system, but you might want to do a google search with the phrase 'The enclosing drive for the volume is locked'. You'll get plenty of hits and a few leads. One persistent suggestion is that the drive was uncleanly unmounted. If that's a possibility, try booting up into Windows 7 and doing a chkdsk on the partition (so long as it's NTFS or FAT32). Or you might be able to use the recovery console on the Windows 7 DVD installer.

---

### Post by tad1073 on 2009-05-25
Menu>Add/Remove>NTFS Configuration Tool

---

### Post by Wiebelhaus on 2009-05-25
Is it Bit locked?

---

### Post by cablejimmy on 2009-05-25
I installed ntfs-config, still have the problem.
I can't find a permissions tab when I go into the partitions properties, and chkdsk says there are no problems.
Just so you know, I have the drive formatted fat32.
And no, it is not bit-locked.

---

### Post by Wiebelhaus on 2009-05-26
That doesn't make any sense , Is this a Windows 7 Partition your trying to access from Ubuntu?

---

### Post by cablejimmy on 2009-05-26
Not really. I made it in gparted, but I first accessed it in Windows 7. Also, I can't access my Windows 7 partition, but that makes sense. Sometimes it locks an external hard drive I happen to have plugged in, too. I'll see if it'll do it again...

---

