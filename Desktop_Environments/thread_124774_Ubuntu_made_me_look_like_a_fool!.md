---
title: "Ubuntu made me look like a fool!"
date: 2006-02-02
forum: Desktop Environments
---

### Post by Zodiac on 2006-02-02
So my I put Ubuntu Breezy 5.10 on my sisters PC so that she wouldn't get any spyware or viruses while away at school.

I told her that Linux was rock solid and she would not encounter any of the errors that she typically saw on Windows.

Silly me. :???: 

2 weeks into her having it she is now getting this error when booting up:

> Checking root file system
/ contains a file system with errors, check forced
 
Inodes that were a part of a corrupted orphan linked list found
 
Unexpected inconsistancy; RUN fsck Manually
(i.e., without -a or -p options)
 
fsck failed. Please repair manually and reboot. Please note that the root file system is currently mounted read-only to remount it read-write:
# mount -n -n remount, rw/

Not only has this rendered her PC unusable, but it is an embarrassment for me. 

Also, I have never seen that error before in my life... can anyone tell me what it is and what I should do? 

Thanks!


P.S. - Did the computer just swear at me???

---

### Post by az on 2006-02-02
To see if the hard disk is defective, from a live cd, run

sudo badblocks /dev/hda1 (if that is the correct partition)

This looks like a hardware problem, and not ubuntu's fault.

---

### Post by kaamos on 2006-02-02
Look here: [http://ubuntuforums.org/showpost.php?p=614550&postcount=2](http://ubuntuforums.org/showpost.php?p=614550&postcount=2)

And to solve future problems: [http://ubuntuforums.org/showthread.php?t=118260](http://ubuntuforums.org/showthread.php?t=118260)

---

### Post by taurus on 2006-02-02
Ask her to see how she shuts down the machine at night!  I just hope she doesn't just push the button to shut it down because that is one way to screw up the machine!!!

---

### Post by Zodiac on 2006-02-02
She has told me that she does not just power the machine off, I believe her. She is a fairly savvy computer user.

I will try what kaamos posted and report back... thanks guys!

---

### Post by taurus on 2006-02-02
If she shuts it down using the shutdown button, then perhaps the HD is on the way out!!!

---

### Post by GrumpyBob on 2006-02-02
I had something similar over the Xmas break on my IBM laptop.  I had frequent system hangs, then a failure to boot with inode problems.  Lots of them.  Fortunately I had a recent backup of data (the default Breezy install had everything on one partition) - I reinstalled Breezy.

My feeling at the time was that this was due to using hibernate (but no eveidence other than it the freezes etc started after i began hibernating the computer and steadily got worse.  I haven't hibernated it since, and I've been 5 or 6 weeks without any problem.

R

---

### Post by Zodiac on 2006-02-02
Okay here is an update in her words not mine:

> It worked! Woot! I do have a question what does hub 1-0:1.0 connect-debounce failed, port 1 disabled mean?? Is that the usb port in the back that doesn't work anymore? Thanks for the help!

Thanks guys, Ubuntu always seems to redeem itself through it's kick *** community ;)!

P.S. - Anyone want to answer her other questions??

P.S.S. - I agree, FSCKFIX should be "YES" by default...

---

