---
title: "DVD mounted twice?"
date: 2005-04-18
forum: Desktop Environments
---

### Post by vaskark on 2005-04-18
When I insert a DVD it appears on my desktop as DVD-ROM Disc so that's fine. If I logout then log back in an extra icon appears called DVD-ROM Disc(2). How can I get rid of it? I tried unmounting the extra one but then they both unmount.

---

### Post by XDevHald on 2005-04-30
Pretty simple actually, do **sudo gedit /dev/fstab **and remove the secondary dvd line.

And also be sure to check the mtab as well, be sure that is not doubled it's self :)

---

### Post by vaskark on 2005-04-30
[QUOTE=BB]Pretty simple actually, do **sudo gedit /dev/fstab **and remove the secondary dvd line.

And also be sure to check the mtab as well, be sure that is not doubled it's self :)[/QUOTE]

I'm confused. Isn't fstab and mtab in /etc ? That's where they are for me. Anyhoo, I've attached both files to this post. In mtab I took out the line referring to my dvd drive (/dev/hdd) and rebooted, but the drive still shows up twice on my desktop. Any ideas?

---

