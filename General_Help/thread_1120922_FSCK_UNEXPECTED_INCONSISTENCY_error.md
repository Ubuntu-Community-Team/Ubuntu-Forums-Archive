---
title: "FSCK UNEXPECTED INCONSISTENCY error"
date: 2009-04-09
forum: General Help
---

### Post by r3aktor.mkd on 2009-04-09
Hi

Im using Ubuntu 8.04 almost a month and today during the boot got the unclean shutdown message, disk checking was running, and it ended up with this log:

--------------------------
fsck 1.40.8 (13-Mar-2008)
/dev/sda6 contains a file system with errors, check forced.
/dev/sda6: Entry 'sessionstore.js' in /r3aktor/.mozilla/firefox/72frgsj0.default (1310731) has deleted/unused inode 1310944.  CLEARED.
/dev/sda6: Entry '5A6A107Dd01' in /r3aktor/.mozilla/firefox/72frgsj0.default/Cache.Trash/Trash/Cache (1507823) has deleted/unused inode 1507989.  CLEARED.
/dev/sda6: Entry 'CA219335d01' in /r3aktor/.mozilla/firefox/72frgsj0.default/Cache.Trash/Trash/Cache (1507823) has deleted/unused inode 1507990.  CLEARED.
/dev/sda6: Unattached inode 1048752


/dev/sda6: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
	(i.e., without -a or -p options)
**fsck died with exit status 4**

Thu Apr  9 20:00:21 2009
------------------------

The few days ago, i had problems with Firefox, I couldnt download anything, e.g. SAVE-OK - and nothing happened.
Soon after , I realised that I dont have sound at all, and Audacious was crashing.

Now,
I tried to run **fsck** in terminal,and i got this:
----
r3aktor@r3aktor-desktop:~$ fsck
fsck 1.40.8 (13-Mar-2008)
fsck.ext3: Unable to resolve 'UUID=f75f154f-a336-4b1c-bb91-bf7dc7dd1661'
----


Could it be a virus?
How to solve this?

Tnx, r3aktor

---

### Post by FXEF on 2009-04-09
To run a fsck, in terminal type:

shutdown -r -F 0

then hit enter.

This tells shutdown you want to reboot and force an fsck upon reboot.

---

### Post by coimby on 2009-04-13
I got the same problem today, after I tried (and failed) to burn a DVD for the first time. 

The problems actually started when I tried to open some files on the DVD which I had tried to write. The system began to act funny, I could not even save the files I had been editing -- most commands failed. So I tried restarting, with the same results as r3aktor got.

This was a scary experience!

CS

---

