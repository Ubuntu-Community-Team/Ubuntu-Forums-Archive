---
title: "Help with login problem and partition, please!  Urgent!"
date: 2006-01-05
forum: General Help
---

### Post by Raos on 2006-01-05
Okay, so I tried logging on like usual after a restart, and I got this message:
> Your session only lasted less than 10 seconds.  If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace.  Try logging in with one of the failsafe sessions to see if you can fix this problem.

We I click on View details (~/.xsession-errors file)
I get:
> /etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "adam"
/etc/gdm/Xsession: Beginning session setup. . .
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0, directory /dev/X will not be created
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/ubuntu:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/ubuntu:
_IceTransMakeAllCOTSServerListeners: failed to open listerner for isc
_IceTransOpen: transport open failed for sco/ubuntu:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco

** (gnome-session: 7906): WARNING **: Unable to read ICE authority file: /home/adam/.ICEauthority

I tried logging in using a failsafe session, but I got the same error message, with less lines in the details, and I think the running out of diskspace may be the problem, since when I installed Breezy, when it was partitioning, I already had Hoary installed, so I chose to create new partitions with the free space, and I thought the new partition was kind of small, but I didn't want to lose my files, so I was planning on transferring everything, and getting everything set up in Breezy, and then eventually deleting Hoary and reallocating the disk space for those old partitions for the new Breezy partitions. Anyway, now this happened, and I can still startup in Hoary, and look at the partition, and I'm downloading the ISO for the live cd, so I can alter the Hoary partitions to make them smaller.

I was planning on following the basic instructures [here in this thread]("http://www.ubuntuforums.org/showthread.php?t=108037&highlight=partition+edit") but it won't let me alter the partitions for Hoary, since I'm currently using them while using GParted, which is why I'm downloading the live CD.  I am having the problem mentioned of being unable to increase the size of the partition, so I'm going to try and do what was mentioned in that thread about creating free space, copying to a new partition, and deleting the old one, and I wouldnt' mind some guidance about that, and I also want to make sure that I'm doing the right thing to fix this problem, or if there's something else I can, there is a good bit fo stuff on Breezy that I'd really really like to not lose, if at all possible, much of which would be really useful for me to have, tomorrow.

If anybody can help with the situation, please, please!  Oh, and what my partitions look like right now from GParted in Hoary:
Partition:               Filesystem      Size(MB)  Used(MB)Unused(MB) Flags
/dev/hda1 (lock)     ext3              18,026     3,654     14,372
/dev/hda3              ext3              8,974      2,706     2,706          boot
v/dev/hda2 (lock)   extended       1,616      ----        ----
    /dev/hda6         linux-swap       416         -----      ----
    /dev/hda5 (lock) linux-swap      1,200    -----          -----

The (lock) means there's a picture of a lock, and I can't alter any of their properties, so I think those are the partitions being used by Hoary, since that's the OS currently running, and the others are (hda3 and 6) are for Breezy.  So yah, any help would be GREATLY appreciated, I'll be checking later before I do anything drastic.

---

### Post by professor_chaos on 2006-01-05
the permissions of the file 
```
/home/adam/.ICEauthority
```
are wrong. I've seen this happen with smb4k before.

Login with the commandline "Ctrl+alt+F1"
then type 
```
 sudo chown adam /home/adam/.ICEauthority
sudo chmod 744 /home/adam/.ICEauthority

```

---

### Post by Raos on 2006-01-05
Oh, wow!  Thank you SO much!  That fixed it completely, and if I tried to edit the partitions I would have likely screwed everything up so much.  Thank you thank you!  You're a complete lifesaver.

---

### Post by professor_chaos on 2006-01-05
Yes, in Linux I had to learn that 1.)everything is a file 2.)everyfile has permissions

When you have a problem, always ask yourself
am I the owner...?
do I have permission...?
 
This is quite a change from windoze, where that answer for most users isn't ever asked because the answer is always YES. 

Glad you did fry your system for such a small thing.;)

---

