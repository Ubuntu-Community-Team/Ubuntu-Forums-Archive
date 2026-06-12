---
title: "Adding new drive at mount point /home"
date: 2006-03-18
forum: Desktop Environments
---

### Post by mitchy_g on 2006-03-18
Hi
I recently completed a new install of ubuntu, and I forgot to mount my 2nd hard drive under /home. I used the "Disks" manager to mount the drive here after the install, but that created problems such as not being able to start any applications.

What do I need to do so that Ubuntu can properly mount the second hdd at /home?

Thanks
Mitch

---

### Post by DiscoKiller on 2006-03-18
could you post the filesystem type and drive details (i.e hdaX. hdcX) and we can figure out ur fstab entry

DK

---

### Post by mitchy_g on 2006-03-18
Ok,

Both disks are ext3.

The primary master (which is in use now):
/dev/hda1 - which is mounted at "/"

The disk i want to add to /home is
/dev/hdb1

Thanks for your help!

---

### Post by Zeroangel on 2006-03-18
Copy all of your subfolders and their files in /home to your new hard drive. Then add or edit the following entry in /etc/fstab:
```
/dev/hdb1       /home     ext3    defaults        0       2
```

If you mount the new drive over the existing home folder then it shouldn't cause problems other than that the content that is currently in the old home folder will still take up space on the drive (though you will be unable to access the files in the old home folder until the new home partition is disabled). 

Its probably a good idea to leave some of the folders that ubuntu needs on the old home directory, just so that should the second drive fail, you will still be able to access the desktop environment.

---

### Post by bonjun on 2006-03-19
i would rather put my 2nd drive on a folder at /home rather that scattering all files of 2nd drive at /home. so  the mount point should be something like this "/home/nameofseconddrive".. just a suggestion.....

what i did is i mount my 2nd drive in /mnt/2nddrivename and made a link at /home/username

---

### Post by mitchy_g on 2006-03-19
Thanks for your help guys

I ran into a few troubles but it was all good after I rebooted it. However a few hidden folders and things wouldnt copy over even with using sudo, but thats ok just a little extra configuring

Mitch

---

