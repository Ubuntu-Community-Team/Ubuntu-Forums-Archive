---
title: "Wubi ate my harddrive"
date: 2009-01-23
forum: General Help
---

### Post by Ibian on 2009-01-23
So i wanted to try Wubi. Seemed like a good deal, no messing around with discs, easy to remove if i got sick of it. Trouble is, it froze during install, probably on account of my semi-broke graphic card (had this issue before with a cd install).
 
It had already reserved the 30 GB i selected during the first part of the install. Naturally, i wanted this space back.
 
So i tried to uninstall it from the control panel. Didn't help. Tried deleting the install folder and rebooting, still nothing. There doesn't seem to be any hidden system files taking up space and at this point i give up.
 
How do i get my disc space back?

---

### Post by step21 on 2009-01-24
What folder do you mean by install folder?

If you didn change the path where you installed wubi the main files taking up space should be root.disk and swap.disk in ubuntu/disks on C. If you really deleted those, did you empty the thrash too? Ofc very likely you have thought of that, just making sure.

---

### Post by Ibian on 2009-01-24
Those files didn't exist after i rebooted from the crash. The entire ubuntu install folder was really quite small, less than 1 GB as i recall.

I don't use the trash can, i delete my files directly. I checked anyway just in case but there was nothing in it.

I tried another install where i set the size to 4 GB, chose restart later and sure enough the install folder had about 4 GB worth of files. Then i uninstalled it instead of continuing with the install and the space was freed back up as it ought to be.

The 30 GB from the first install are just gone and nothing is taking up the space. The drive shows 76.9 GB out of 114 GB used. Selecting everything in the root folder and hitting alt+enter shows 46.9 GB worth of files and folders. Never seen anything like it.

---

### Post by step21 on 2009-01-24
Mmmh, maybe some weird fragmentation issue? Try running windows checkdisk and the defragmentation tool (warning, at least the defragmentation can take quite some time)

My reason for believing this might help: Before the reboot these files should have been present, and normally the linux installer has no way of removing them ... so I suspect that when it was writing to the disk while crashing that something on the disk got corrupted, but the windows disk tools should fix that.

---

### Post by Ibian on 2009-01-24
No dice. The scan reported no errors and defragmenting did nothing.

---

### Post by WatchingThePain on 2009-01-24
Are you using Vista? if so it's easy to get the space back. Right click 'my computer' then manage, storage, disk management.
In XP you might need a third party program like partition magic.
Perhaps fdisk in DOS and delete the partition there?.

---

### Post by Ibian on 2009-01-24
I'm experimenting on an old system, so XP. I got stuff on the disk in question and no room on the other disk for it, so messing with partitioning is probably out.

I figure i'll just buy a big USB stick on monday, move my stuff to the laptop and then format the drive, but it would be nice to be able to fix it without such a blunt (and non-free) approach.

---

### Post by ago on 2009-01-24
Run chkdsk /r and look for a hidden folder called C:\found000 or similar
You need to change the explorer settings to view hidden files in windows.

---

### Post by Ibian on 2009-01-24
No such folder anywhere on my system and chkdsk didn't do anything either.

---

### Post by irfan9727 on 2009-01-25
Try some disk-space explorer program on windows (like, [http://www.jam-software.com/freeware/index.shtml](http://www.jam-software.com/freeware/index.shtml) maybe?) then see the file sized 30gb and then delete it. Or maybe that's system restore "back-up"-ing that file?

:KS

---

### Post by Ibian on 2009-01-25
That did it. I was able to delete the hidden found000 folder from within that program, freed up about 28 GB. There are still 2 GB worth of hidden files in the root folder which for some reason i can't delete, but whatever it's fine now. Thanks.

---

### Post by step21 on 2009-01-25
the hidden file in the root folder sounds like the windows page file(s) even if you coul delete them windows would just recreate them.

---

### Post by Ibian on 2009-01-25
Right, of course. I forgot where i had it on this system for a moment there. Problem solved then.

---

### Post by jered6323 on 2009-02-08
I'm having sort of the same problem. Wubi installed fine, and uninstalled fine, but I still haven't gotten the disk space back. TreeSize free found folders "FOUND.000" all the way through "FOUND.006". But all folders total 0mb.

Edit: TreeSize found all the way through "FOUND.016", but the biggest of all the FOUND folders was 32mb. I dedicated 8gb to Ubuntu, so where is it?

---

### Post by tixetsal on 2009-02-12
Hey guys.  I had the exact same problem.  I had uninstalled/reinstalled ubuntu via wubi several times on Vista Ultimate x64, as I was "learning the ropes" (aka ruining my install trying to use hybrid SLI w/ubuntu).  Curse those nvidia drivers!!!  (Off topic - If anyone has figured out how to use hybrid SLI, pl let me know!)  Anyway, I was missing 90 GB of HD space.  I am a windows admin @ a major university in the SE, so I am no noob in Win, but I could not find the missing HD space ANYWHERE!  After struggling with the problem in my mind for 1/2 day, it finally hit me.  System Restore!  If you have already followed the instructions here (run uninstaller, manually deleted C:\ubuntu and all related backup dirs, run chkdsk /f /r) and you are still missing HD space.  TURN OFF SYSTEM RESTORE!  I got my 90 GB back, thank God.  I hope that this helps someone out there.  Good luck!

---

### Post by Darkmage09 on 2009-02-12
To the above poster. Since this is Windows XP the OP (Original Poster) has stated. Windows XP does not make big shadow copies (System restore files) Vista takes 15% of your HD for the shadow Copies. 

Now to the problem. Can you do a System restore before the problem had occured? I know I had some problems with that on Vista. It had taken up allot of my HD space.

Good Luck :)

---

