---
title: "My H120 makes nautilus crash! Help!"
date: 2007-05-17
forum: Desktop Environments
---

### Post by jigantor on 2007-05-17
Hope this isn't the wrong place for this post...apologies if it is!

I've been happily using an iRiver H120 with Rockbox for about a year now, No problems to speak of until last week when I tried to delete a fair amount of the music on it. It didn't delete properly (didn't show up in Ubuntu but still showed up on the player itself) and Ubuntu promptly decided it was a read-only device. Taking the advice of a friend, I ran chkdsk (like fsck.vfat but better according to this guy) in Windows and fixed up a whole lot of non-contiguous stuff (and deleted the non-faulty files with the intention of starting again from scratch). It now mounts and reads fine in Windows, chkdsk claims there are no problems with it.

BUT: in Ubuntu, every time I try to access the drive nautilus crashes and I have to reboot. I can browse the drive in the terminal, but as soon as I try to alter anything the terminal freezes. I'm running Ubuntu Dapper, GNOME, on a Core2 Duo with 1GB RAM and 60GB free HDD space.

Can anyone help me out here? How can I make it work? My train rides are really boring without music!

Cheers,
Tim

---

### Post by crazybilly on 2007-08-17
man.  My (full) h100 is slowing nautilus to a crawl.  It's awful.  What's up w/ this?

---

### Post by crazybilly on 2007-08-23
update:  turns out it wasn't my 120 bringing nautilus to its knees.  It was fstab--just before I plugged in the h120, I had edited fstab to mount a smb share on a local folder.  

But using smbfs resulted in horrific timeout that made me want to cry.

Changing smbfs to cifs solved the problem.  

Probably not your problem, but the point of the story is that if somebody else comes looking for help on an h120 slowing down their system, they might want to think back to the last couple changes they made in their system--while it might seem related, it very well might not be.

---

