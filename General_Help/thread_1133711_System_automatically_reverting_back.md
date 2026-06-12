---
title: "System automatically reverting back??"
date: 2009-04-23
forum: General Help
---

### Post by humandraydel on 2009-04-23
I feel silly posting this, but I'm at a loss for what to do.  Twice in the past week my computer has "reverted" back a few days.  I've lost programs that I installed and in one instance my password was actually changed back to an older password.  In the system logs there are gaps of a couple of days.  

Now the paranoia in me hopes I haven't been breached and I've considered a fresh install but I'd hate to do that if not necessary.  It doesn't seem to me that a hacker would uninstall a game and revert my password.  

Any ideas?

---

### Post by humandraydel on 2009-04-23
I've searched everywhere (forum and the web) and still can't find any clues.  

Another thing I noted was that files on my separate /home partition were not deleted during this automatic revert.  It appears as though only the / partition was reverted?

---

### Post by humandraydel on 2009-04-23
So I just got home from work and turned on my computer....and the program that was gone is now there again.  The gaps in the system logs are gone.  I feel like I'm going crazy!

Is this some sort of hardware failure?

---

### Post by humandraydel on 2009-04-28
Well, I found out what the problem is so I'm going to detail it here in case someone else has a similar problem.


I had used dd to clone my root partition to a second hard drive for system restore purposes.  I didn't realize that the UUID was also cloned.  When booting it was purely random as to which hard drive (and therefore copy of OS) was being referenced by the UUID (since both hard drives/root partitions had the same UUID).  

The fix, then, is to either use the "/dev/sda1" nomenclature in fstab and grub OR use tune2fs to generate a new random UUID after cloning a partition.


[http://paulgoscicki.com/archives/2007/05/ubuntus-uuid-schizophrenia/]("http://paulgoscicki.com/archives/2007/05/ubuntus-uuid-schizophrenia/")

---

