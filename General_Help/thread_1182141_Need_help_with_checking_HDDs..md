---
title: "Need help with checking HDDs."
date: 2009-06-08
forum: General Help
---

### Post by DestinedCruz on 2009-06-08
Hey guys, I would like to know if somebody could help me with this.

I work for a PC service store that also sells used systems to businesses in the area.
We are just moving into sellng pallettes of systems (15-25 at a time) with no-OS, as well as the standard pre-loaded systems we carry.
Rather than load Windows on each an every one of these systems to test the hardware, I thought that using an Ubuntu live CD was a much better alternative, as this pretty much fully tests the optical drive (to boot Ubuntu), the system memory (to carry and use the OS), and the audio/video (obviously).
The only problem I have run into is an effective way to check the condition of the HDD drives on these systems. I can basically create and delete an NTFS partition, but that really isn't enough.
I was wondering if anyone could help me regarding shell scripts to check the drives (sort of like a scandisk/checkdisk deal), or some way to stress the drives for a certain amount of time to make sure they don't fail.

I know due to the nature of unix-based systems, Scandisk etc. isn't necessary, but for what I'm doing it is absolutely necessary. I know my way around a Linux distro for my own use, but I don't have the knowledge required for this.

Any ideas? Any help would be massively appreciated.

---

### Post by bertmanphx on 2009-06-08
Hello,
The newest version of Fedora has a new Gnome-disk-utility that will display SMART data of the drive if enabled in the BIOS.

For that matter though, Ubuntu will do the same thing from the command line.

IF the hard drives are SMART capable, it would show you something.....

bertmanphx

---

### Post by DestinedCruz on 2009-06-08
I'm not sure if that is exactly what I'm looking for. I need something along the lines of possibly creating a partition with data and then checking it for consistency. Maybe not quite that extensive. But I'm not so much looking for information on the drive as making sure it's not a bad drive. I can create partitions all day long but it's not going to tell me if the drive isn't going to give problems during regular use.

For example one option I have is to run SeaTools on each and every drive, but pulling each and every drive from 60-80 systems and running a Long Generic scan (which can take 30+ minutes for an 80gig drive), then putting them back into the systems and running a live CD really isn't efficient. I need some way to test the drives at the same time as I test everything else.

---

### Post by DestinedCruz on 2009-06-09
Anybody have any ideas?

---

