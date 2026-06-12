---
title: "Mount 'Local Disk' easily in Unity?"
date: 2011-07-04
forum: Desktop Environments
---

### Post by dave0109 on 2011-07-04
I've just upgraded from 10.10 to 11.04 and am still very much getting used to Unity. I'll keep perservering for a while. However, I can't work out how to mount the local disk's NTFS partition easily.

With 10.10 (and all the others before it), I could mouse click on the Ubuntu icon, select Places, then 'Local Disk'.  The disc would be mounted and I'd have access to the files I need.  Quick and easy.

Now with 11.04, after much messing around, I've found that I can click on the 'Home' icon in the launcher, which opens up Nautilus.  In there I can then change the left hand view from my default of 'Tree' to 'Places' and from the list of places I can select 'Local Disk', finally changing my view back to 'Tree'.  A long winded process.

I don't seem to be able to "stick" the 'Local Disk' icon in the launcher, and can't see another way of accessing it quickly.  I'm trying to be positive about the upgrade, but it's not easy.

Any ideas?

---

### Post by dave0109 on 2011-10-17
Wow, forgot I posted this.

Just in case anyone else has the problem, I ended up (a few months later) adding the disc mounter applet to the top panel.  This always showed an icon for Local Disc, so I was able to mount and unmount as required.

---

### Post by Mobby on 2011-10-17
Just in case it helps and is another option for you...

Take a look at this guide - [here]("https://help.ubuntu.com/community/Fstab")

Following that guide will mean the partitions are always mounted (at logon or possibly earlier, not 100% sure sorry). This will mean the NTFS partitions you've added to the FSTAB will always appear as a "drive" icon in the Unity panel on the right (the dash?).

Cheers,
Mobby

---

