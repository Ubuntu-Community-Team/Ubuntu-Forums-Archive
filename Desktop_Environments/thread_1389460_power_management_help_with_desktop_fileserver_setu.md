---
title: "power management help with desktop fileserver setup"
date: 2010-01-24
forum: Desktop Environments
---

### Post by ljwobker on 2010-01-24
SO... I was a solaris admin in a former life (like Waaaay former) and I'm now a networking engineer... for fun I decided that instead of just buying an off-the-shelf NAS box I would re-learn some of the linux world and teach myself ubuntu and RAID and all that good stuff... which wasn't incredibly difficult given that I understand RAID concepts pretty well and the forums have all sorts of helpful stuff.  HOWEVER... it seems that power management on ubuntu systems is a very deep very black maze of a lot of stuff that doesn't seem to work the way it should.   ;-)

So the most general question is:  is there a good webpage/howto/wiki somewhere that talks about power management capabilities on ubuntu and what works, what doesn't, etc?  I've been searching in lots of various places for about 3 weeks and haven't really been able to find anything that's cohesive on this topic.

The more specific questions are around my long-term goals... which is to have my existing system function as a part-time RAID server... ideally I want something that basically goes to sleep after 15 minutes of no activity, and then responds to a wake-on-lan signal and comes back up long enough for me to do whatever backup/restore/file IO needs to be done... then goes back to low-power mode.  
The system I'm working with is a Zotac IONITX Atom mobo with a set of Hitachi 1TB SATA drives as the file storage.  The boot/rootFS device is just a generic 4GB USB key with 9.10 running.

Along the way I'd really like to learn some of the specific sub-parts of this, like being able to explicitly control disk spinup/spindown, and figure out what the difference is between "suspend" and "standby" and learn more about the ACPI bits that seem (somehow) to be at the root of all this power goodness. 

So... the long post aside -- anyone got good pointers that I could start reading?  ;-)

---

