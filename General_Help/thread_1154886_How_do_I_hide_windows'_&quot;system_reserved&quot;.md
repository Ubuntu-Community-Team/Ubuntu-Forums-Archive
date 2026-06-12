---
title: "How do I hide windows' &quot;system reserved&quot; partition?"
date: 2009-05-10
forum: General Help
---

### Post by Fzang on 2009-05-10
Windows has a 200 mb partition with bootloader and repair commands. This partition shows up in ubuntu as well...

How can I hide it from showing up in ubuntu?

---

### Post by BslBryan on 2009-05-10
Hello, Fzang. :-)

Partitions are a computer thing, not an OS thing.  So, while your hard drive is partitioned for dual-boot, so you have Windows and Ubuntu, the partitions exist on the hard drive.

Since this is the case, when viewing them all partitions will show up.  This is a feature that really cannot be turned off, to my knowledge.  

I hope I've been of some help to you, and I apologize if I've misunderstood your question.

Best to you, Fzang. :-)

---

### Post by DeMus on 2009-05-10
> **Fzang said:**
> Windows has a 200 mb partition with bootloader and repair commands. This partition shows up in ubuntu as well...

How can I hide it from showing up in ubuntu?

How did you mount it in the first place?

---

### Post by Fzang on 2009-05-10
I'm not mounting it. It's simply showing up in nautilus because it wants to :)

I know this doesn't affect me or anything else in any actual way, I'm just so picky about aesthetics and I would kill to have a shiny desktop :p

---

### Post by mmnike on 2010-06-13
Hello everybody here is my solution.

How to hide windows system reserved partition:

1.Go to Ubuntu Software Center
2.Under system search for Gnome Partition Editor and install it
3.System->Administration->GParted
4.Right click on the system reserved partition and click manage flags
5.Check hidden

---

### Post by Citizen_Kane01 on 2010-07-27
> **mmnike said:**
> Hello everybody here is my solution.

How to hide windows system reserved partition:

1.Go to Ubuntu Software Center
2.Under system search for Gnome Partition Editor and install it
3.System->Administration->GParted
4.Right click on the system reserved partition and click manage flags
5.Check hidden

THIS IS NOT A GOOD IDEA!!!!

My Windows (7) installation was corrupted. It is trying to recover itself as I write.

A better solution can be found on this thread:

[http://www.uluga.ubuntuforums.org/showthread.php?t=1305383&page=2](http://www.uluga.ubuntuforums.org/showthread.php?t=1305383&page=2)

---

### Post by IanVaughan on 2011-12-05
> **Citizen_Kane01 said:**
> THIS IS NOT A GOOD IDEA!!!!

My Windows (7) installation was corrupted. It is trying to recover itself as I write.

A better solution can be found on this thread:

[http://www.uluga.ubuntuforums.org/showthread.php?t=1305383&page=2](http://www.uluga.ubuntuforums.org/showthread.php?t=1305383&page=2)

Does this really screw up the drive then?
It sounds like a nice idea!

---

### Post by Mark Phelps on 2011-12-05
> **IanVaughan said:**
> Does this really screw up the drive then?
It sounds like a nice idea!

YES -- messing with the flags on the Win7 boot partition screws up the drive.

It's a much better idea to use the FSTAB solution as that only affects mounting the partitions from inside Ubuntu and doesn't mess with the partition flags themselves.

---

