---
title: "Saving in MacOSx HD"
date: 2009-05-07
forum: General Help
---

### Post by frcol on 2009-05-07
I must save a file into a MacOSx system HD, but I don't have the permissions to do that.

It shows me that the owner of the folder is a "501" user, and I can't create this user in Ubuntu.

---

### Post by kanikilu on 2009-05-07
Do you know if your Mac OS X partition uses journaled HFS+? If so, you can only read, not write to it.

Are you dual-booting? If so, you can boot into OS X and use diskutil from the terminal (or Disk Utility from Applications/Utilities) to disable journaling.

There's other information out there, but here's a blog post that deals with it:

[http://castyour.net/node/40](http://castyour.net/node/40)

Note, those instructions apply to doing this to an external hard-drive, not the primary partition for OS X. If that's the case here, you'll probably need to boot up with your Mac OS X installation disk and run the Disk Utility from there since the partition needs to be unmounted.

To be honest, I've only done this with external drives, so you might want to search around some more to see if there might be any negative effect from disabling journaling on the main OS X partition...

---

### Post by frcol on 2009-05-07
The partion is hfs+ (Ubuntu Partition Editor), I don't know if it's journaled.
yes I'm dual boot (XP, Ubuntu and MacOsx(boot)).

thanks for your replau]y.
If I found a way to access the Mac HD by the OSx Terminal or save by Ubuntu it would solve my problem.

---

### Post by kanikilu on 2009-05-07
I believe journaling is turned on by default - or at least it is in 10.5.

Do you have your installation DVD? That's what you'd need to be able to disable journaling on that partition.

---

### Post by frcol on 2009-05-07
> **kanikilu said:**
> I believe journaling is turned on by default - or at least it is in 10.5.

Do you have your installation DVD? That's what you'd need to be able to disable journaling on that partition.

Yes, I do.

I´ll try using the DiskUtility from the DVD, but I´m afraid to delete any data.

---

