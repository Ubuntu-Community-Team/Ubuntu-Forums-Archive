---
title: "Filesystem sharing in dual boot system"
date: 2012-12-08
forum: Desktop Environments
---

### Post by algrossi on 2012-12-08
Good day:
I have a laptop with Windows-7 and Ubuntu 10.04 running dual boot. I use the same set of user files in both environments but it's a chore trying to keep them in sync. Is there a way of having a common filesystem which contain one set of user files and accessible by the programs in both OS's? I am now using Ext2ifs but it's crude.
Thank you for any help
Al

---

### Post by entropy1 on 2012-12-08
I used to have this problem too.  My solution was to use GParted (from a live CD or USB) to create an a new NTFS partition. I labeled the new partition NTFSdata.  In it I created the following folder structure "Users/myname". In "Users/myname/" I created a Documents folder.

Then I booted into windows and told it to use this new location for Documents.  (See [http://windows.microsoft.com/en-us/windows7/Redirect-a-folder-to-a-new-location]("http://windows.microsoft.com/en-us/windows7/Redirect-a-folder-to-a-new-location") for details.) Then I booted into Ubuntu and replaced ~/Documents with a sym link pointing to /media/NTFSdata/Users/myname/Documents.  You can also edit /etc/fstab to automatically mount the NTFSdata partition when you boot Ubuntu.

Now both OS use the same files and there is no need to sync.

An additional benefit is that if you reinstall windows or Ubuntu, it shouldn't mess with the NTFSdata partition (but back up NTFSdata anyway; you can't be too careful!).

---

### Post by oldfred on 2012-12-08
I also have a shared NTFS data partition. I have my Firefox & Thunderbird profiles, photos for Picasa and many data files. Now that I am not booting XP I put new data in a LInux formatted data partition, but have not yet removed my NTFS shared partition.

       new 
[http://kb.mozillazine.org/Moving_your_profile_folder](http://kb.mozillazine.org/Moving_your_profile_folder)
[http://support.mozillamessaging.com/en-US/kb/Profiles](http://support.mozillamessaging.com/en-US/kb/Profiles)
[http://www.mozilla.org/support/thunderbird/profile](http://www.mozilla.org/support/thunderbird/profile)
Firefox
[http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox](http://kb.mozillazine.org/Transferring_data_to_a_new_profile_-_Firefox)

    
       Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)

---

### Post by algrossi on 2012-12-08
THank you very much for your insightful input. This is a lot to take in immediately, since I've only been using Ubuntu for about a year...
I can see that all the info oyu posted is good and I will have to carefully implement it in stages. I have no problem partitioning - the only thing I was uncertain of, is Ubuntu writing into an NTFS filesystem, but I am presuming that Ubuntu is proliferate enough to do that. The old Unix System-V I used to work on could not do such a thing. I will follow your instructions and will post my results - I can be confident that it's going to work out great.
Have a great day - and thank you again
Al

---

### Post by Bucky Ball on 2012-12-08
Ubuntu will read/write to NTFS without issue.

---

### Post by offgridguy on 2012-12-08
This file sharing is something i plan on trying in the near future, thank's for the insight.

---

### Post by oldfred on 2012-12-09
The only issue with NTFS is that is does not support Linux ownership & permissions. Whatever you mount partition as becomes a default setting. As long as you do not try to copy system files that need specific ownership and permissions then it works well. 

       Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

    
       [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from Morbius1 - suggest using templates instead. Post #6
copy & paste template & edit to your specifics.

---

### Post by NightsShadeQueen on 2012-12-09
You need the package ntfs-3g to write to NTFS from ubuntu; this should come installed, but if it doesn't, it'll give you a permissions error.

You could also mount your Windows partition in Ubuntu and directly symlink from Ubuntu's ~/Documents to Windows's Documents (and Downloads, Music, etc.)

---

### Post by Mister08 on 2012-12-09
> **NightsShadeQueen said:**
> You need the package ntfs-3g to write to NTFS from ubuntu; this should come installed, but if it doesn't, it'll give you a permissions error.

You could also mount your Windows partition in Ubuntu and directly symlink from Ubuntu's ~/Documents to Windows's Documents (and Downloads, Music, etc.)

This is my favorite method. It can be a pain migrating to the folder being so inefficient. But it saves you the trouble partitioning the drive. Another method I use is using Dropbox to automatically sync documents from either folder, that way no matter what computer or OS I use I can access my documents with very little trouble.

---

### Post by algrossi on 2012-12-13
Well I managed to setup the "Shared-NTFS" as a Primary partition and Ubuntu reads and writes to it with no problem, Windows-7 cannot see the partition. I used MiniTool partition program from Windows, to give the partition a Drive Letter "D" but as soon as it tells me it has done it, it reverts back to "*:Shared-NTFS". I've been through the process many times but it won't accept a drive letter. Sometimes the difficult part of a project is the most unsuspecting.
If someone has more insight I would love to attempt this further, but at the moment I'm almost out of ideas.
Al;

---

### Post by algrossi on 2012-12-16
Looks like some more scanning the net allowed me to locate a solution. It's quite weird but as long as it works, who's to complain.
[http://social.technet.microsoft.com/Forums/en/w7itprohardware/thread/35eee15b-69c0-4927-856a-3f0622893074](http://social.technet.microsoft.com/Forums/en/w7itprohardware/thread/35eee15b-69c0-4927-856a-3f0622893074)
This site explains the procedure.
Thanks to all
Al

---

### Post by Bucky Ball on 2012-12-16
Please mark thread as Solved if you are satisfied you have found a solution. This will help others do the same. ;)

---

