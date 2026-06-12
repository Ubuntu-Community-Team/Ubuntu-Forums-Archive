---
title: "Upgrade from 8.0.4 to 8.10 epic fail."
date: 2008-12-04
forum: Desktop Environments
---

### Post by SterLo on 2008-12-04
*Note that I just realized I posted this in the wrong place...should probably be under the Upgrades section - sorry.*

So I preformed the synaptic upgrade to 8.10 from 8.0.4
It asked to overwrite some files I let it do what it needed to do.

Then it got to the end and said that it failed upgrading and that the system was in unstable condition.

Then it rebooted and did a file system check.
Which failed.

Now it says (these are the important bits anyway):
> /dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY
(i.e., without -a or -p options)
fsck died with exit status 4

* An automatic file system check (fsck) of the root filesystem failed. A manual fsck must be performed, then the system restartded. The fsck should be performed in maintenance mode with the root filesystem mounted in read-only mode.
* The root fileystem is currently mounted in read-only mode. A maintenance shell will now be started. After performing the system maintenance, press CONTROL-D to terminate the maintenance shell and restart the system.
Give the root password for maintenance (or type Control-D to continue):

BUT - there's no root password...that was never set (I think)...so I can't get in...unless there is a default password.

Anyone know what steps I can take from here? :confused:

---

### Post by SterLo on 2008-12-04
So here is what I am trying right now.

I got a Live CD - booted into it.
I ran fsck -f /dev/sda1 - it's currently in progress.
Hopefully this will help.

---

### Post by SterLo on 2008-12-04
So after running the FSCK I rebooted - the system then loaded into Ubuntu in low graphics mode...I told it to use the default graphics because it wouldn't allow me to do a manual config.

So it appears that I lost my O/S settings - I not longer have my xconfig - but the software and files are still intact.

So - craptastic but not as craptastic as it could have been...

Anyone want to tell me why the heck Ubuntu doesn't make you set a root password upon install?

---

### Post by SterLo on 2008-12-04
So I have gone ahead and done the following:
> sudo passwd root

I however noticed that although this changes the root password - the actual root account is disabled - so that's...useful.

At the same time - I am still boggled by not being asked ever to set the root password.

---

