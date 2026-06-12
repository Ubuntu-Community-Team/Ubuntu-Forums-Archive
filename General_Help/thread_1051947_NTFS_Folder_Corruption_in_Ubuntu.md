---
title: "NTFS Folder Corruption in Ubuntu"
date: 2009-01-27
forum: General Help
---

### Post by tatemononai on 2009-01-27
Ok, I am having a problem that's driving me absolutely insane.  I'm running Ubuntu 8.1 as my primary OS.  I have a second hard drive (NTFS) mounted which has Windows on it.

I spent many hours yesterday backing up a bunch of CD's to this drive through Ubuntu.  A bunch of picture CDs.  I created a folder named "BACKUP" and copied away.  All the copying was done through Ubuntu onto the NTFS drive.

This morning I get up and find that the data is corrupted.  Ubuntu will not let me go into the "backup" folder anymore.  It thinks the backup folder is a true-type font file.  Windows doesn't see anything named "backup" at all.  When I search the drive for *.jpg I get nothing.  Last night I had about 10GB of images in that backup folder.  Where the heck did they all go?

---

### Post by drs305 on 2009-01-27
A couple of things to check: 

Are you sure the files were copied onto the other mounted drive? If the drive wasn't properly mounted, the data might have been copied instead to the *mount point folder*. If the data was in the folder instead of copied to the drive, it would not be visible if the drive was subsequently mounted. Unmount everything and then check the mount point folder to see if the data is "hiding" there.

If you know the name of a specific file, with the second drive mounted, do a search for the file with the following command. It will search your entire system for the file:
```

sudo find / -iname <filename>  # example:  sudo find / -iname mypic.jpg

```

---

