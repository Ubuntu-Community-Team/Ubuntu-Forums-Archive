---
title: "resizing partions on dual boot"
date: 2006-06-07
forum: Desktop Environments
---

### Post by frogotronic on 2006-06-07
Hi,

  I installed ubuntu 5.10 BB a few months ago on my XP laptop.  I used GParted LIVE CD to resize the windows partion.  My HDD is 40 GB and I made the ubuntu size 10 GB and XP 30 GB.  Everything was (is) great.

  I would like to resize the partions to be even (20 GB ubuntu + 20 GB XP).  [I still need XP for work, etc].  Anyway, Can I use GP Parted LIVE to resize the partions again?  If so, how can I accomplish this?  Should I resize the XP partion (NTFS) first?  OR the linux side?  If I do the XP side first, will ubuntu automatically resize the "it's" side from 10 GB to 20 GB?

  Any advice would be appreciated?

Thanks,
-CH :confused:

---

### Post by aysiu on 2006-06-07
Is it something like this now?

/dev/hda1 Windows 30 GB
/dev/hda2 Ubuntu 10 GB

And you want it to be this?

/dev/hda1 Windows 20 GB
/dev/hda2 Ubuntu 20 GB

That won't be so easy. See, when you resize Windows from 30 to 20, it'll leave a 10 GB gap *before* Ubuntu, and you can't add space to the beginning of a partition, only to the end.

You could always try using PartImage to back up the Ubuntu partition, delete it, resize, and then use PartImage to restore the Ubuntu partition, but that's a bit involved...

[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

I think your best bet would be to free up 10 GB off the Windows partition and just mount that as an extra data partition in Ubuntu.

---

### Post by frogotronic on 2006-06-08
[QUOTE=aysiu]Is it something like this now?

/dev/hda1 Windows 30 GB
/dev/hda2 Ubuntu 10 GB

And you want it to be this?

/dev/hda1 Windows 20 GB
/dev/hda2 Ubuntu 20 GB

That won't be so easy. See, when you resize Windows from 30 to 20, it'll leave a 10 GB gap *before* Ubuntu, and you can't add space to the beginning of a partition, only to the end.

You could always try using PartImage to back up the Ubuntu partition, delete it, resize, and then use PartImage to restore the Ubuntu partition, but that's a bit involved...

[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html)

I think your best bet would be to free up 10 GB off the Windows partition and just mount that as an extra data partition in Ubuntu.[/QUOTE]

Yep, That's my setup.  hmm...bummer on the resize - but I think I'll try the PartImage.  Thanks! :-k

---

