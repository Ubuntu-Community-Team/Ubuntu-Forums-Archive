---
title: "Programs shut down by themselves"
date: 2009-03-25
forum: General Help
---

### Post by mrl777 on 2009-03-25
Hello,

I'm running Ubuntu live (for security reasons) and I have noticed that programs shut down by themselves, such as Firefox and the movie player.  The CD rom turns on and POOF, the program shuts down.  I restart it and some time later, POOF, it shuts down.

Has anyone experienced this?

---

### Post by evilaim on 2009-03-25
Ok, So what exactly would be the security needs for a live CD?  Live cd's aren't meant to be ran for long durations.  It could possibly be that you're running out of physical or virtual memory and it's just closing it.

If I were you, I'd personally install ubuntu on to a flash drive, where it could run as a full system.  There are many tutorials on how to do it, and you could use even a 1 gig stick.

Just search google and I'm sure you'll find something along those lines.

---

### Post by mrl777 on 2009-03-25
> **evilaim said:**
> Ok, So what exactly would be the security needs for a live CD?  Live cd's aren't meant to be ran for long durations.  It could possibly be that you're running out of physical or virtual memory and it's just closing it.

If I were you, I'd personally install ubuntu on to a flash drive, where it could run as a full system.  There are many tutorials on how to do it, and you could use even a 1 gig stick.

Just search google and I'm sure you'll find something along those lines.

The reason I'm doing this for now is I think someone has installed a rootkit in a flash, such as the BIOS or maybe the ATI graphics card.  I'm doing research into this.  As for getting it onto a flash stick, the problem is if I've got a rootkit in some flash then it could, in thearory, get tinto the mem-stick as some point.  If, however, I could write protect the mem-stick then it could be an alternative.  However, there's nothing to prevent something from crawling into the system while it's running and flashing the memory again.


I have a definite bone to pick with the hardware manufactures.  Why why why why would they not jumper protect their flash memories.  I've designed hardware and I can tell you this stuff is so simple to do.

We could put an absolute end to the rootkit hiding in flash problem if manufactures would just jumper protect their flash roms.  Yet I read endless discussions about this issue on the internet.  People musing about how to prevent it.

Simple solution:

On the motherboard you put a switch  on the back that says BIOS/CMOS Lock/Unlock. On the display controller you do the same.  When one wants to upgrade the BIOS or change the systems settings they simply reach around to the back of the machine and flip the switch.

Also, it would be simple enough to write software that would take a snapshot of all the flash systems in the computer and store them to file, which would be burned onto bootable CD.  Then, if one suspected a problem, one would just boot up the CD and and run FlashCheck and it would compare all the flash roms in the system to the ones on the CD. If they didn't match then you've got a problem.  You would then reflash the rom from the old image.

Also, why not just make hard drives with read only switches on them, so if you wanted to protect your OS after installation you would just flip the switch to read only.

There's so many practical solutions.  Little switches that say "Lock/Unlock".

---

### Post by evilaim on 2009-03-25
You do realize that you're on an ubuntu forum right?  Stuff doesn't install in the Ubuntu system without asking you for a password.  Specially on flash drives.  I really wouldn't worry about 'rootkits' in ubuntu.  If one is installed then you really aren't careful enough.  Don't enter passwords for stuff you don't do and you shouldn't have any issues.

---

