---
title: "Help!  Deleted files with script!"
date: 2009-05-23
forum: General Help
---

### Post by kooldino on 2009-05-23
I ran a script from the shell that didn't go right due to the random nature of how kubuntu names external disks.  The script did an rm -rf in the wrong directory, and managed to do some damage before I could ctrl+c it.  I lost an entire directory plus a few files.

They are not in the trash bin.  Is there any way I can get these back?

---

### Post by glotz on 2009-05-23
No, I'm afraid.

---

### Post by baseface on 2009-05-23
[http://www.linuxquestions.org/questions/linux-newbie-8/help-how-to-recover-rm-rf-files-443236/](http://www.linuxquestions.org/questions/linux-newbie-8/help-how-to-recover-rm-rf-files-443236/)

---

### Post by kooldino on 2009-05-23
I'm recovering a lot with PhotoRec (testdisk didn't work), but it's just dumping a bunch of files into one directory.  It's going to take me eons to wade through it all, rename them, and put them in folders.

Is there a tool that will undelete entire directories and save me days of manual labor?

---

### Post by kooldino on 2009-05-25
Holy crap - story of the year...

So I removed the disk from the machine and plugged it into an XP machine to try some Windows recovery tools (since it was an NTFS disk).

Upon bootup, XP said that the volume was "dirty" and was going to fix some file table entries.  When completed, the machine finished loading windows.  I checked the contents of the drive and voila - everything was back to how it was before the rm -rf!!!!  Hooray for windows and NTFS for fixing this.  It made my week!

---

