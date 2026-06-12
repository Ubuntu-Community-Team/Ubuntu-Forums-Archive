---
title: "Error while booting up."
date: 2009-01-25
forum: General Help
---

### Post by kaldor on 2009-01-25
Recently, for the last few weeks, every time I boot up Ubuntu it needs to do a "routine scan of drives /dev/sda2". But, the problem is, after it hits about 1%, this message comes up: 
```
*Checking root file system..
1240
fsck 1.40.8 (12-Mar-2008)
/dev/sda2 contains a file system with errors, check forced.
Checking drive with /dev/sda2: 0% (Stage 1/5, 2/1401)
Checking drive with /dev/sda2: 0% (Stage 1/5, 17/1401)
Checking drive with /dev/sda2: 0% (Stage 1/5, 18/1401)
Checking drive with /dev/sda2: 0% (Stage 1/5, 19/1401)
/dev/sda2: Inodes that were part of a corrupted orphan linked list found.

/dev/sda2: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY (ie, without -a or -p)
fsck died with exit status 4

Checking drive /dev/sda2: 1% (stage 1/5, 21/1401)

*An automatic file system check of the root file system failed.
A manual fsck must be performed, then the system restarted.
The fsck should be performed in maintenance mode with the root file system mounted in read only mode.

A maintenance shell will now be started.
After performing system maintenance, press CONTROL-D to terminate the maintenance shell and restart the system.

Give root password for maintenance

(Or type control-D to continue):


```

What can I do about this?

---

### Post by kaldor on 2009-01-25
No ideas?

---

### Post by kaldor on 2009-01-25
No help is available? :(

---

### Post by hansdown on 2009-01-25
Hold tight kaldor.

Someone with more experience than myself will help.

---

### Post by kaldor on 2009-01-26
Nothing still.. ? (bump)

---

### Post by hansdown on 2009-01-26
Hi Kaldor.

I hope this helps.

[http://ubuntuforums.org/archive/index.php/t-316345.html](http://ubuntuforums.org/archive/index.php/t-316345.html)

Do you have a live ubuntu cd or a copy of gparted?

You need to run fsck while your dard drive is not in use.

Sorry to give you bits and pcs. of info, but this is new for me too.
[https://answers.launchpad.net/ubuntu/+question/36305](https://answers.launchpad.net/ubuntu/+question/36305)

---

### Post by hansdown on 2009-01-26
You will need to use sudo fsck /dev/sda2

 	 
[http://www.backports.ubuntuforums.org/showthread.php?t=256949](http://www.backports.ubuntuforums.org/showthread.php?t=256949)

The following thread is best.

[http://ubuntu-utah.ubuntuforums.org/showthread.php?t=1011140](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=1011140)

---

### Post by kaldor on 2009-01-26
There is no chance of this doing any damage is there?

I do not want to risk losing the things I have :(

And yes, I do have a Live CD and gparted as well.

---

### Post by hansdown on 2009-01-27
There is always a certain risk. Due to my inexperience,I usually do a fresh install. It fixes most problems.
If you google```
 how to manually run fsck in ubuntu
```
You'll see that in some cases, this warning can point to a failing hard drive.

---

### Post by kaldor on 2009-02-27
Reviving the topic!


I think I am just going to simply wipe the partition. I just backed up some files on a USB storage device that I will be needing.

If I use gparted to erase the correct partition, will this problem go away?

If I start again and install from scratch, will everything go smoothly?

Last and not least; Which release is better? Hardy or Intrepid?

Thanks!

Edit: The reason I plan to just start over is because I do not have the time to go fixing things/tweaking when there is a chance of things not going over well; I just want to get rid of this problem. Is this an Ubuntu problem or is it my laptop?

---

### Post by kaldor on 2009-02-28
*another bump*

Sorry about the number of bumps everyone! I just want this answered. :)

---

