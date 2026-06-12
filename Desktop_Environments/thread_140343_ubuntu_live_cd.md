---
title: "ubuntu live cd"
date: 2006-03-06
forum: Desktop Environments
---

### Post by DarkManX4lf on 2006-03-06
hi, i got the ubuntu live cd for my laptop which currently has windows installed, and i wanted to know if it is possible using the live cd to view/browse files from my windows installation, and how would i be able to do it?

---

### Post by aysiu on 2006-03-06
Yes, but it'll involve some command-line use, and if your Windows installation uses NTFS, it will be read-only (you can't modify files).

This is a rather involved explanation.
[http://www.psychocats.net/linux/mountwindows](http://www.psychocats.net/linux/mountwindows)

The quick and dirty would be Applications > Accessories > Terminal ```
sudo mkdir /windows
sudo mount -t ntfs /dev/hda1 /windows
gksudo nautilus
``` and then navigate to the /windows directory.

If you're in the habit of doing this often, you should probably use Knoppix instead, since this will automount and open your Windows partitions at the click of a mouse.

---

### Post by DarkManX4lf on 2006-03-06
thanks it worked, i needed to backup some files from the windows partition

thanks again

---

### Post by aysiu on 2006-03-06
No problem. If you can get ahold of a Knoppix CD, those CDs are wonderful for recovery. Ubuntu's live works, too, but it's not really designed for recovery.

Glad it worked out for you.

---

