---
title: "apt-get program not found"
date: 2007-08-25
forum: Dell  Ubuntu Support
---

### Post by Mejedin on 2007-08-25
I was trying to switch users, but I forgot the password to the other user.  I then pressed the "Quit" button.  The screen then went black, after a few second I could see my mouse, but nothing else was loading.  I then held down the power button on my computer and I forced it to shut down.  Upon rebooting the computer informed that the disk was not cleanly unmounted and it was performing a disk check (as it usually does when I force shut down).  But before it was 100% finished, it stopped and told me there is a duplicate or missing block. I then told me a string of three or four numbers (I can copy down the exact error if it is necessary.).  I tried again and it performed the disk check again and it got to a further percent, but then prompted the same error.  I tried again and found no luck, then I booted in recovery mode.  It did the same thing and prompted the same error.  But then it told me that I was missing the "apt-get" program.  It then told me that I needed to type:
apt-get install apt
and when I did that said that I don't have apt-get (obviously).
     My question is, is the only solution to this problem installing the apt-get program? If so, how might I do that?

---

### Post by Dark Star on 2007-08-25
Same happened with me :( nor 1,2 or 3 but many times but the way told to correct failed every tme. So I reinstalled the OS over time :(

---

### Post by ticklecricket on 2007-08-26
I have the exact same issue!!

When I get to the terminal I just typed "reboot". the screen flashed a few times then loaded gdm. I don't know what's borked or how it's fixed, but that's a working work around for me.

---

### Post by Dark Star on 2007-08-26
> **ticklecricket said:**
> I have the exact same issue!!

When I get to the terminal I just typed "reboot". the screen flashed a few times then loaded gdm. I don't know what's borked or how it's fixed, but that's a working work around for me.
Eh? How did you went to Terminal ? The error comes before GDM theme . i,e while boting.. if apt-get missing you can' even reach to GDM there :(

---

### Post by Mejedin on 2007-08-26
The exact error is:
Duplicate or bad block is use!
/dev/hdb1:Multiple-claimed block(s) in inode 1489056: 2290190 2290191 2290192
/dev/hdb1:Multiple-claimed block(s) in inode 1489080: 2290190 2290191 2290192

And after that it loads more error and does what it did when I loaded in recovery mode (I did not know this earlier because I didn't wait long enough).  Then it has a place where you can enter commands.  I tried to type "reboot" and it loaded more text, but then it went to a cyan screen that said:
Could not start the X server (your Graphical environment) due to some internal error.  Please contact your system administrator or check your syslog  to diagnose.  In the meantime this display will be disabled.  Please restart the GDM when the problem is corrected.

I rebooted and tried the exact same thing, but instead of taking me to the cyan screen with that error, it asked me to log in (even though the whole thing looked like DOS).  I logged in and it was Terminal.  I tried "apt-get install apt".  It didn't work.

---

### Post by notwen on 2007-08-26
First off is this on a  dell machine? Just wanting to verify that you're posting in the right forum. =]  Secondly, Ive gotten you're issue when my /etc/fstab is no longer correct.  Have you made any new partition prior to  your issue?  You may want to run a LiiveCD w/ gParted or just d/l the gParted LiveCD itself an first check to see if your partition which contains  grub has the boot flag.  After my system had similar issues, I needed to re-add the boot flag and modify my /etc/fstab to resolve my situation.  Hope your issue is more simple than this, but good luck regardless. =]

---

### Post by Mejedin on 2007-08-26
No, my computer is not a dell.  Perhaps I should have posted in the general help forum.  My apologies for not doing so.  My hard drive is partitioned but that has not caused any problems so far.  I was using ubuntu perfectly for a while before this incident.

---

### Post by Mejedin on 2007-08-27
Would I be able to get the program on put it on a flash drive and then stick it in my computer and grab it from the terminal?  If so, what is the code for doing so?  If that doesn't work, would it be possible to simply put the live CD in my CD-ROM and boot from that then copy the program over to my hard drive?

---

