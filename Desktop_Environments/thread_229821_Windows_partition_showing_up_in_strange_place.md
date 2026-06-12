---
title: "Windows partition showing up in strange place"
date: 2006-08-05
forum: Desktop Environments
---

### Post by Midway on 2006-08-05
Hello all, new to Ubuntu and Gnome and have a weird problem I have never ran across before.
 
I am dual-booting with XP and after the install I went to "Computer" but it did not show hda1 (XP partition).  The Linux partition is labeled "filesystem".  When I clicked on it I found a "Windows" folder along with the other linux folders.  I can click on it and access my XP partition without any probs though.

Will this cause problems later on?  Is there a way to fix this so it will be a separate drive icon?

Thanks! :)

---

### Post by H.E. Pennypacker on 2006-08-05
This is odd...very odd.  The Windows partition, of course, can't be on the inside of the Ubuntu partition.  

Go to System > Administration > Disks.  Switch to the partitions tab.  How many partitions show up on that list, and how many should there be?  Is hda1 showing up as being the size you expect it to be (a good way of identify the partition you're looking for is looking at its size)?  

Go through that list and see if there's something strange.

Can you also post up your fstab (/etc/fstab)?

---

### Post by Midway on 2006-08-05
Everything looked ok in Disks Manager except for a 6GB free space I don't remember seeing before.  My /windows, /, /home. and swap are showing.

Here is my fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda4       /home           ext3    defaults        0       2
/dev/hda1       /windows        ntfs    defaults,auto,nls=utf8,umask=007,gid=46 0       1
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdb1       /media/backup   ext2    defaults 0 0

Also if my hdb1 entry looks a little weird, it is the only way I could get Ubuntu to see the 2nd hard drive (only done this once before and can't remember how it was done.

[IMG]http://img135.imageshack.us/img135/245/screenshotvo5.png[/IMG]

---

### Post by H.E. Pennypacker on 2006-08-05
Ah, I see what is going on, and what went wrong where.  Ideally, your Windows partition will show up alongside /root when you go to "Computer" (its better to create a "Computer" link from the desktop - use Gnome Tweak Tool for this).  Take a look at the following screenshot:

[[IMG]http://img213.imageshack.us/img213/5529/screenshot8bk3.th.png[/IMG]](http://img213.imageshack.us/img213/5529/screenshot8bk3.png)

You'll see several partitions, including Windows (the 11GB partition) and /root (which is named File System).

At some point in time, your fstab shows, you created a mount point for your Windows partition on the inside of /.  Notice that next to HDA1, it says /windows.  That means there is a folder called windows under the / directory.  Hopefully this makes sense.  

Simply creating a new mount point for Windows should solve this problem.    Unfortunately, manually editing fstab is the only way this can be done, because there is no GUI.

Do gksudo gedit /etc/fstab (I prefer using leafpad, not gEdit).

Edit the hda1 line to have /media/hda1 as the mount point (the second column).  The next time you start your computer, Windows should no longer appear under root, but instead next to root as "hda1" just as my screenshot shows, but on my harddrive, Windows is hda2.  Ignore that part.

It's good that you posted your fstab.  Make sure, whenever working with something as important as the fstab, to create a backup.  Save it in another directory, and when you see that nothing has gone wrong, you can get rid of the backup if you must.

---

### Post by Midway on 2006-08-05
Thanks, that did the trick though I had to go a few more steps to get it to work right.  After I rebooted I noticed my Windows drive was showing up like it should.  But when I clicked on it, it informed me that only root can access it.  So I did the "chmod 777" thing and rebooted just to get the same message again.  I then added "user" to the fstab entry, rebooted and this time I got the "mount point does not exist".  I just went through this trying to get it to see my 2nd hard drive so I did the "mkdir /media/hda1", rebooted and now I can access my Windows partition.  I noticed that the windows folder was still in my root (it was empty) so I rmdir that to get rid of it.

I only tried Ubuntu once (I think it was Warty) and it hosed my XP partition so I have been gun shy of Ubuntu since then.  When I was ready to try Dapper, I googled around for "XP/Ubuntu dual boot" and found some instructions.  I must have misunderstood one of the steps and that what caused the "/windows" mount point.  Other distros did not ask for a mount point for windows during installation and it had me confused.

So that has fixed the last quirk I had, the others I fixed by searching on this forum (such as getting the HPLIP Toolbox working).  I am on dial-up so I took my tower to work to do updates and automatix.  I also needed a couple of KDE apps I liked (such as digikam and amarok).

Many thanks for your help! :D

---

### Post by H.E. Pennypacker on 2006-08-06
Ubuntu doesn't ask for a mount point for anything during the installation.  I can't find an explanation for why Windows was given that mount point.

To browse Nautilus as root (all permissions), do sudo nautilus.  That will open up Nautilus as root, and you should be able to do anything.

---

### Post by Midway on 2006-08-07
The installer would not let me go any further until I created a mount point for windows. The drop down menu only had / , Home,Var and other linux folders to choose from. The wiki does not mention this so I searched on google and found some instrutions (can't find it now or I would give you the link).  The author mentions running across the same thing and the way I understood it I was supposed to put "/windows" in the box for the mount point.  I would like to get clarification on this in case I have to reinstall for some reason (which I hope doesn't happen anytime soon, lol).  I would like to know what to put in this box next time (maybe /dev/hda1 ?).

I missed my "Super File Manager" in KDE so after doing another search on this forum I have made a "root nautilus" file manager program. :)

---

### Post by Midway on 2006-08-07
This is not the website I found (still searching), but it basically mentions the same thing:

[http://users.bigpond.net.au/hermanzone/p3.htm]("http://users.bigpond.net.au/hermanzone/p3.htm")

The author is using the alternative installer in this case. Scroll down to Fig. 28ntfs.

---

### Post by Midway on 2006-08-07
Nevermind, that was in reference to a FAT32 "share" partition.  It appears that Ubuntu saw the XP partition and mounted it at /media/hda1 (as shown in figure 11ntfs).  But this didn't happen in my case, it showed up in the list of partitions to be mounted. Also it did not see my 2nd hard drive either and I had to make a mount point for it as well.  Anyway, it works great now and Ubuntu seems pretty stable. :)

So if I do have to do a reinstall and if it asks me again, I will mount it at /media/hda1 and see if that works.

---

