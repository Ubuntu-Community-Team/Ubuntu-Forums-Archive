---
title: "Wubi add-virtual-disk confusion"
date: 2009-06-21
forum: General Help
---

### Post by fosa on 2009-06-21
Ubuntu 8.10
Intel 64bit
Wubi virtual disk installation

So I wanted to increase the virtual disk from 40gb to 100gb, and found the wubi-add-virtual-disk script.  I ran it as sudo sh wubi-add-virtual-disk /home 100000  and it started doing its thing.  Kind of slowly.  Actually, it was going so slowly that after a while I thought it had locked up on a particular file and killed the process.  I just couldn't see it taking that long to copy a 300mb file.  

So now there is a /home folder with 84gb of free space, 32mb of confirmed disk files, and some unreadable content which is hopefully 15gb in size.  This leads me to believe the terminal wasn't updating which files it was transferring.  I'm not sure what else might have been going on there.

There's also the /home.backup folder with the 31gb of files that I'd like to make sure are saved.

There are a few things i'd like to know:
1) How to check the total size of a virtual disk
**2) Is it Ok to delete everything in my new /home folder and just cp from /home.backup to /home ?  Will that ensure the boot process works well and all that?**
3) If there is 15gb tied up in unwritten files, will deleting the contents of the new /home free up that space or will it get lost in some swap place?

Thank you to any who can take a moment and help me out, I really appreciate it!

---

### Post by fosa on 2009-06-21
Solved it:

sudo cp -v -r home.backup/fosa home/fosa 

then as referenced from this thread:

[http://ubuntuforums.org/showthread.php?t=371052](http://ubuntuforums.org/showthread.php?t=371052) to use ricardos method of 4 chmod/chown lines

Hope this helps someone in a similar situation that I was.

---

