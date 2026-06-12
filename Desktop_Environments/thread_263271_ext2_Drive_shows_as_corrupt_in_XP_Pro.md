---
title: "ext2 Drive shows as corrupt in XP Pro"
date: 2006-09-22
forum: Desktop Environments
---

### Post by Tom Brokaw on 2006-09-22
I'm dual-booting 6.06 and XP Pro.  Went to transfer some files from my main XP box to this XP install.  Opened up my "music" folder, which is on an ext2 drive.  Only goes to "D", (Dead Kennedys to be exact) and the folders that do show up are inaccessible, show as empty, or have the wrong files in them.  Mike Oldfield was in Daddy Yankee, for example, and the files were inaccessible.

When I try to right-click for properties, it freezes upon clicking OK to exit properties.  I've let it get to the blue "Windows is shutting down" screen, which takes about 5 minutes, and then it seems to freeze completely and I have to do a hard reset.

This is a second hard drive.  I have installed the ext2fs drivers for XP and had had no problems up til now.  My third and fourth hard drives, also ext2, are fine, knock on wood.  The music drive is accessible from Ubuntu, or at least it was the last time I booted.

I've tried setting the drive letter to "none" and rebooting, and then resetting it to the appropriate letter (F) and rebooting.  It didn't seem to accept it, though; it froze again.  Upon rebooting the letter was F, but the same problems remain.

I thought I had formatted these drives as ext3, not ext2, but I can't be sure without a reboot, so I'm posting here first.  Will edit as necessary.

Summary:
ext2 drive's data shows as corrupt in XP.
Appears to be fine in Ubuntu.
Other ext2 drives appear to be fine in both OSes.

I have a considerable amount of music on here and would really, really prefer not to have to copy it over again.

Thanks.

---

### Post by Tom Brokaw on 2006-09-23
Bump.  Any ideas?  I realize this is more of an XP problem than a Linux problem, but I sure would appreciate some suggestions if anyone has any.

---

### Post by alecjw on 2006-09-23
Firstly, Mike Oldfield rocks.

Try upgrading your version of ext2 for windoze.
Also, fsck your hard disk from the livecd to check it for errors. If you have a seperate /home partiton where this is stored, try telling ubuntu to check it on bootup by changing the last no on the row of /etc/fstab to 2, or if there's already a row ending in 2, then make it 3 and so on.

---

### Post by Tom Brokaw on 2006-09-27
Hi alecjw,
thaks for the reply and sorry for the long response time.  I will try that as soon as I learn how to use fsck (still a noob).  There was a forced file check one of the times I booted to Ubuntu, and it came up fine.  However, I have no idea which disk it actually checked.  I'll learn more and give it a try when I get a chance.

---

