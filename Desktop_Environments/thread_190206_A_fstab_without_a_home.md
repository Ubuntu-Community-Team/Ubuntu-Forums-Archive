---
title: "A fstab without a /home"
date: 2006-06-06
forum: Desktop Environments
---

### Post by angrydill on 2006-06-06
Here's something I can't figure out, if anyone could kindly venture a guess as to what's going on...

I installed xubuntu 6.06 yesterday from the "alternate" CD (since my friend's PC on which I installed it has too little ram [128 MB] to install from the live CD).

I partitioned the 8.5 GB HDD as such:
[LIST]
[*]hda1 - 5 GB ext3, mount point /
[*]hda5 - 256 MB swap
[*]hda6 - 3.2 GB ext3, mount point /home
[/LIST]

Everything seemed to install fine, and it booted into a fully functional XFCE desktop (which, though I'm a KDE guy, looks pretty cool).  After checking it out for some time, I shut it down for the evening.

Tonight I booted it up, and when I tried to log in at the DM prompt, I got a message that the home directory was **missing**.  I logged in failsafe, and noticed that the /home partition was not mounted; nor was it listed in /etc/fstab.  I mounted it manually with "[FONT="Courier New"]mount -t ext /dev/hda6 /home[/FONT]" and the partition worked just fine.  I then edited /etc/fstab using (sudo) vi and added the missing partition.

When I rebooted, I had the same problem **again;** /home was missing from fstab.  To make sure I wasn't imagining things, I edited it again, and after writing the changes I cat-ed it on the console to ensure my changes were there.  After reboot, it was just like before; missing /home.

Any idea what might be happening?  Is there anything in the [x]ubuntu startup scripts that might overwrite or modify the fstab?

One other thing that seems strange, is that the filesystem type for hda1 (according to fstab) is "unionfs", rather than ext3 as I had specified.  I'm not really familiar with this but from googling it seems that its not typically used for permanent partitions, but usually for live CD partitions.

Any suggestions would be greatly appreciated.  Thanks!

-a.d.-

---

### Post by angrydill on 2006-06-07
In case anyone has the same problem, I didn't figure it out.

I believe the install was botched.  Perhaps it's related to the "unionfs", but according to /etc/mtab, the /etc/fstab file was "mounted" on another (virtural?) partition residing off of /var/tmp. 

Bottom line, i re-installed and let xubuntu wipe the disk and auto-create a single partition layout.  Worked like a charm.

-a.d.-

---

