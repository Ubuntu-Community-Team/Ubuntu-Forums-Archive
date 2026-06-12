---
title: "GRUB works fine when rebooting, but breaks if machine loses power"
date: 2010-06-10
forum: Desktop Environments
---

### Post by lpreams on 2010-06-10
Ok, so I've got a desktop that my dad custom built himself. He's a hardware engineer for Intel, so I trust him to make a reliable system. Now, this system WAS built for, and runs wonderfully, better than systems with twice the specs, Windows XP. Now, I've been trying to set up a dualboot with Ubuntu. Everything worked fine. I installed Windows first so GRUB would get written to the MBR. If I rebooted, GRUB worked fine. The problem was when I powered off. If the machine lost power, whether it be from an outage, me turning it off, Windows hibernating, whatever, GRUB always broke. 

At this point, I decided to experiment. I used boot and nuke to do a 7-pass wipe of the hard drive, then installed Ubuntu with as many default settings as I could. Guided partitioning, industry-standard ext3, everything (Ubuntu 9.10, btw). Same problem. If the system lost power, I had to put in a live cd and reset grub with the command line. 

Since then I've reverted back to just Windows XP, to save myself the headache of using the live cd every few days. I can't even use hibernate to save time rebooting into Windows. The only suggestion I've gotten is to check the voltage on my button battery on the motherboard, but as my system time is always correct, I doubt that's it. Has anyone else had a similar problem and, if so, how did you fix it? 

Just in case anyone's wondering, this was all done with both Ubuntu 9.04 and Ubuntu 9.10. I haven't tried the 10.04 LTS, but it's next on my list, and then I might try Debian, Fedora/Red Hat, or Suse. Not sure yet. 

Also, this is, as I said, a custom system. 250 GB SATA, 40GB UltraATA, 1GB RAM, 2.8GHz dual-core CPU

---

