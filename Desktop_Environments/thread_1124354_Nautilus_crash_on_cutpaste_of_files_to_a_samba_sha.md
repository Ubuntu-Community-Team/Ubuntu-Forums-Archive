---
title: "Nautilus crash on cut/paste of files to a samba share"
date: 2009-04-13
forum: Desktop Environments
---

### Post by wolfie2x on 2009-04-13
Here's my problem:
If I mount (samba) a FAT32 folder of a WinXP sp2 machine on my ubuntu intrepid and do a simple file move (cut/paste) from ubuntu to the samba share, nautilus crashes. It's always recreatable (not adhoc). Other operations such as copy/paste works fine.

Can someone pls test this and let me know? Is this a known/reported issue?

I'm on intrepid fully up-to-date as of 13-Apr-09.
Doing sudo force_start=1 /etc/init.d/apport restart and recreating the crash didn't bring up any crash report.

---

### Post by caseykelso on 2009-06-01
I have the same problem.  Did you have any luck resolving the issue?

---

### Post by wolfie2x on 2009-06-02
> **caseykelso said:**
> I have the same problem.  Did you have any luck resolving the issue?

Nop no luck. I simply copy/paste and then delete instead of move. 
I'm on Jaunty now; yet to test if the problem exists.

---

### Post by Jammer_UK on 2009-06-11
Have you got DropBox for linux installed and running?

---

### Post by wolfie2x on 2009-06-11
> **Jammer_UK said:**
> Have you got DropBox for linux installed and running?

Yeah I do! Is that the cause of the crash!?

---

### Post by Jammer_UK on 2009-06-12
I had exactly the same issue on another version of Linux. Removed Dropbox and all works perfectly, with regards to cut & paste in nautilus to a SAMBA share. I have tried 0.5 and the lastest 0.6 release of dropbox and the problem still occurs. I suggest you test by uninstalling dropbox and see if the problem still occurs.

I have emailed dropbox support and not yet heard anything.

---

### Post by Xantane on 2009-06-22
Same issue with Dropbox, its creating a segmentation fault when it tries to copy
------------


Initializing nautilus-dropbox 0.6.1


(nautilus:9213): GLib-CRITICAL **: g_strsplit: assertion `string != NULL' failed

(nautilus:9213): GLib-CRITICAL **: g_strv_length: assertion `str_array != NULL' failed
Segmentation fault

---

### Post by loeppel on 2009-06-25
Same issue here. Jaunty 9.04 and Dropbox 0.6.510.

---

### Post by Youresorock on 2009-07-14
There is a launchpad thread about this.  It's marked as a dup for another bug, but it's pretty obviously the dropbox bug if you read the comments.

[https://bugs.launchpad.net/ubuntu/+bug/395942](https://bugs.launchpad.net/ubuntu/+bug/395942)

No solution posted however.

---

### Post by pasQualle on 2009-08-02
Haven't looked in the launchpad post jet, but same problem here. But for me it's not a samba share, it's cuting/pasting files to an ftp server.

---

### Post by Schnitty on 2009-11-13
i had the same issue on jaunty, but only starting around mid-october.  i did not have dropbox or ubuntu one installed then.  i upgraded to karmic, same problem.  i wiped the drive and did a fresh install, same problem.  then i installed dropbox, which did not appear to help or hurt the problem.

i did just run another experiment tho - i started an FTP server on the file share i was trying to move to and tried cut/paste to that - i had the same issue.

does anyone know if an FTP cut/paste follows the same code path as an SMB cut/paste?  i'd think no, but i'm not an expert on this

---

### Post by prainho on 2010-01-24
> **Xantane said:**
> Same issue with Dropbox, its creating a segmentation fault when it tries to copy
------------


Initializing nautilus-dropbox 0.6.1


(nautilus:9213): GLib-CRITICAL **: g_strsplit: assertion `string != NULL' failed

(nautilus:9213): GLib-CRITICAL **: g_strv_length: assertion `str_array != NULL' failed
Segmentation fault

I've the same problem and I confirm nautilus crash because Dropbox. I've removed dropbox and now it's working ok again. any one knows how to solve this problem???

---

### Post by gespertino on 2010-04-20
[http://forums.dropbox.com/topic.php?id=18389](http://forums.dropbox.com/topic.php?id=18389)

Nautilus-Dropbox is fixed. This file isn't automatically updated by dropbox but I guess it's reasonable to expect that the next stable version will solve the problem.
At the moment you can download the installer for nautilus-dropbox and works fine.

---

