---
title: "copy or move file/directory to another partition or drive?"
date: 2009-01-25
forum: General Help
---

### Post by SeePU on 2009-01-25
Okay, I am feeling pretty silly an stupid for having to post this but I am so confused at the moment.  Is it Ubuntu?  I would like to think so since I have moved files before with no problem.  But, it's taken me so long and I had to use a GUI method to get it done.

If you're experienced, adept or otherwise skilled at this part of Linux, by all means, please help and instruct.

Case/Task:   moving or copying (usually, I will copy the file since it is safer and is the cautionary way to do it in case there is a mishap).  I want to copy a file or directory (or both - meaning files and directory together) to another partition on another drive.   

The problem is that the drive is not mounted yet but I use sudo fdisk -l so I can see which partition I can copy to.  I don't always remember but I know which drive is available (I just don't always recall what device node it's assigned (e.g. sdb1 etc.).  

I thought I need to establish a mounting point and then create a temporary directory for it and mount it there.   Is that correct?  Does it matter where I create the temp directory?  I usually call it temp or tmp.  But, no matter what, I couldn't copy the file and I had a bunch of output that prevented the task from being completed. 

Perhaps, someone could present an example or a link so I can read the steps.  I will google and search the forums in the meantime.    Another thing:  I got tired of using sudo every time so I used 'sudo su.'  Is that okay?  I guess I am one of those Ubuntu users who is always contemplating abandoning Ubuntu because I just can't stand sudo.  I admit it.  At least, I am being honest, right?

I just thought that K/Ubuntu was close enough to the other Linux distros that I could tolerate it (isn't it still related enough to Debian?).  I thought the GUI extras and 'up-to-date' situation was appealing.

Anyway, enough about that.  Can anyone help me get a grasp on copy/move because even though it should be simple enough, it's an achilles heel for me for some reason.

---

### Post by sdennie on 2009-01-25
You were able to copy the files with "sudo su"?  In that case, it just means you mounted the destination with permissions such that only root had write access to it.  You'd have to give more information like, the filesystem type of the destination drive and the output of /etc/fstab and the output of "groups" to get more help.

---

### Post by SeePU on 2009-01-25
> **sdennie said:**
> You were able to copy the files with "sudo su"?  In that case, it just means you mounted the destination with permissions such that only root had write access to it.  You'd have to give more information like, the filesystem type of the destination drive and the output of /etc/fstab and the output of "groups" to get more help.
Well, I tried using sudo first but since I have to type it out each time (it didn't work)....

The partition it was in was formatted ext3 and so is the other partition in the other drive.   It shouldn't be a problem.

---

### Post by sdennie on 2009-01-25
If the other partition is ext3 and you are having problems manipulating it without sudo, it probably means that the owner of the files on the external drive doesn't have the same UID as your current user.  ext3 isn't ideal for removable storage that you plug into multiple machines for this very reason.

---

