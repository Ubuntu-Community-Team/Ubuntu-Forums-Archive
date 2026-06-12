---
title: "Problems with install"
date: 2007-01-17
forum: Development CD/DVD Image Testing
---

### Post by pashby on 2007-01-17
Hi there

I am having problems installing the Herd-2 release.

I downloaded the Desktop version and made the disk from the ISO image.

When installing from the image all went well until the partitioner tried to format my nice new harddrive. The message was something akin to can't format the partition - aborting.

I tried to setup a boot partition ext3 of 100 meg, a root partition of 10 gig reiser, a home partition of 36 gig reiser and a swap partition of 1 gig.

That's my experience so far.

On an ASUS A6J with gig ram 40 gig HD 2400 Duo Pentium processor.

This machine has and is now running Dapper without a problem.

Peter

---

### Post by pochu on 2007-01-18
Please report a bug at Launchpad and provide any info that can be useful, like your hardware, logs...

Thanks
Pochu

---

### Post by pashby on 2007-01-18
Hello again

Read somewhere to use a terminal and execute ubiquity.

I did and it installed with no problems.

It seems that the installer on the live CD may be the source of the problem.

Peter

---

### Post by pochu on 2007-01-18
Hi pashby.

Nice to hear that! Can you please report that running "sudo ubiquity" from the terminal has worked for you?

I think there is a bug with the same problem as yours, you should report the workaround there.

Thanks
Pochu

---

