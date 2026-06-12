---
title: "system not starting after restart"
date: 2024-09-30
forum: Desktop Environments
---

### Post by safix on 2024-09-30
Hello,
So I've been using Ubuntu desktop on my Lenovo T440 laptop for the past 8 years without any issues. The machine is on all the time and was working rock solid.


Suddenly a few months ago after a restart the system does not start. There are many errors, but I think the most noticeable one is that the hard drive is mounted in read-only mode.


I've tried replacing HDDs, downgrading to Ubuntu 21, flashing BIOS. Nothing helps.
I start with a fresh new installation, give it a few days, next restart everything goes black, with loads of errors.


I managed to get the journalctl log by remounting the hard drive via the command line.


Can anyone here please help me figure this out?

I've attached the journalctl.log to this thread.

---

### Post by yancek on 2024-10-01
> I think the most noticeable one is that the hard drive is mounted in read-only mode 

A very common reason for that happening is due to filesystem corruption.  Did you get any positive results when you ran a filesystem check on the various partitions?  Are they all Linux filesystems? An online search for running a filesystem check on Linux will give you many results and most of them will give the various options and how to use them.

---

### Post by safix on 2024-10-07
> **yancek said:**
> A very common reason for that happening is due to filesystem corruption. Did you get any positive results when you ran a filesystem check on the various partitions? Are they all Linux filesystems? An online search for running a filesystem check on Linux will give you many results and most of them will give the various options and how to use them.

Thank you for the reply yancek!
I've done some very **basic** filesystem checks which didn't raise any flags. The partitions are all Linux filesystems. Every time this happens, I use the Ubuntu installation wizard to remove all partitions, and create a new one for a complete fresh install.

If this is a common [COLOR=#000000]filesystem corruption scenario, then it looks like the file system gets corrupted [/COLOR]**[COLOR=#000000]consistently [/COLOR]**[COLOR=#000000]e[/COLOR][COLOR=#000000]very time.

Do you have any ideas what can be the cause? I can't seem to be able to use this machine anymore. Every time I install a fresh Ubuntu, the file system gets corrupted after a few days.[/COLOR]

---

