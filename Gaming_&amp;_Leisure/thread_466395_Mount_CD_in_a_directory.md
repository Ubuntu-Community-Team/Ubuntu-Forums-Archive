---
title: "Mount CD in a directory"
date: 2007-06-06
forum: Gaming &amp; Leisure
---

### Post by Quicky on 2007-06-06
Not specifically a gaming & leisure question, but I'm trying to install Football Manager 2007 from a CD by following the instructions at winehq here:
[http://appdb.winehq.org/appview.php?iVersionId=7729]("http://appdb.winehq.org/appview.php?iVersionId=7729")

There is an instruction there which states 'Mount the Football Manager 2007 CD in a directory. In this directory, launch the FM2007 installer'.

My question is, how do I mount the CD in a directory? 

Cheers

---

### Post by meng on 2007-06-06
Everything gets mounted in a directory! You will probably find that your CD is automatically mounted, and the located is probably /media/cdrom
So, drop to terminal:
cd /media/cdrom
wine setup.exe
(substitute "setup.exe" with whatever the installer program is called)

---

### Post by Quicky on 2007-06-06
Cheers!

The instruction is a redundant turn of phrase if everything gets mounted in a directory. Why not say "Run setup from the CD's mount point"? It suggests that you can mount the CD *outside* of a directory.

---

### Post by meng on 2007-06-06
Yes, **OR** the setup instructions try to cover the possibility (especially on other and older distros) that the CD is not automounted upon insertion. In which case the user would have to mount it manually (obviously mounting it to a directory because it's not possible to mount anything outside of a directory). (But then again, a user that knows **how** to mount a CD would surely realize that it would have to be mounted before any files could be accessed ...

By the way, I assume my advice helped you? Do you still have a problem?

---

### Post by Quicky on 2007-06-06
Thanks - I was aware that I'd find the contents in /media/cdrom0/, but I think it was the fact that the instructions were telling me to mount it in a directory that made me assume it had to be mounted in an alternative location. That and the knowledge that I've never manually mounted anything since using Ubuntu - all my external media is mounted automatically (as it should be) - I needed a second opinion!

Anyway cheers, you were spot on mate - its installing as I type.

Nice one.

---

