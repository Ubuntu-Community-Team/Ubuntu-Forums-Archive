---
title: "Evince causes CPU to heat up and system to shutdown"
date: 2011-10-13
forum: Desktop Environments
---

### Post by themaheshrs on 2011-10-13
Hi!

I have Ubuntu installed and running on 5 different systems at home. I agree all of the systems are kind of old (dual-core CPUs, 2GB RAM, 200+ GB hdd, etc). But, I am seeing the following behavior on ALL of my systems:

When ever I open a fairly large PDF file (say > 10 MB), and try to browse through the pages of that file, my system shuts down automatically. After some investigation, I found out that Evince, the default PDF reader in Ubuntu (10.10) eats up all the CPU causing the CPU to over heat leading to the automatic shutdown.

I installed the free Acrobat Reader on two of my systems and have seen behavior similar to what I describe above.

So, my questions are:
1. Has anyone else noticed this behavior?
2. Is there a solution to this behavior?

Regards
Mahesh

---

### Post by mcduck on 2011-10-13
Clean your computer, make sure there's no dust in the CPU's heat sink or fans, and that all the fans are working. IF there's lots of cables restricting the air flow in the case, sue some zip ties to clean them up.

The processor is built to be able to handle sustained 100% load without any problems. Failing to do so is *always* a hardware-related issue.

That being said, a 10MB PDF file shouldn't cause much of a CPU load, does this happen with all that large files, or only with certain ones? And also what kind of graphics cars you have, and do you have working drivers for it installed? Non-working graphics drivers could be a reason for high CPU load when scrolling documents.

---

