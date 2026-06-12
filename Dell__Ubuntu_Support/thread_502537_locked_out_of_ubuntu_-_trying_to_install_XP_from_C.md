---
title: "locked out of ubuntu - trying to install XP from CD - hard drive &quot;locked&quot;?"
date: 2007-07-16
forum: Dell  Ubuntu Support
---

### Post by agility1 on 2007-07-16
I'm resurrecting a year old machine that we don't remember the admin password on.  It is a Dell Dimension 9150 running Ubuntu 5.0 I believe.  I'm trying to boot the machine from the CD using a windows xp disc, but get a msg that the hard drive is unavailable.  On a restart, I use F12 to get to the bios system setup which sees the drive.  The hard drive diagnostics give out the comment "Drive 0 - ST......AS - Pass".  

I checked the bios system setup and there are no passwords in place at that level.  Is there a feature in Ubuntu that locks the drive even though I'm doing a CD ROM boot up?

Ron

---

### Post by kc2keo on 2007-07-17
> On a restart, I use F12 to get to the bios system setup which sees the drive

F12 to get to the BIOS setup? I thought it was F2 to get to BIOS setup and F12 for boot screen. Maybe common mistake.

> Is there a feature in Ubuntu that locks the drive even though I'm doing a CD ROM boot up?

Not that I know of.


Why are you trying to install XP? Are your intentions aimed at erasing the drive to install a new version of Ubuntu, remove the Ubuntu pass, or install XP and forget Ubuntu.

Are you able to get to the XP installation menu? Maybe you have SATA drives and XP has a hard time reading them or something.

If you think your BIOS has a password on it you may either open up the machine and use the password jumper to reset the password or take the BIOS battery out for 5 mins and put it back in which should clear the CMOS BIOS chip.

Other than that I am quite unclear what your intentions are. Please try to be more specific.

--kc2keo

---

