---
title: "Booting faster after the upgrade?"
date: 2009-04-28
forum: General Help
---

### Post by lodp on 2009-04-28
A fresh install of Jaunty on my laptop shaved an amazing 40 seconds off the boot time. My desktop on the other hand, which I upgraded from Intrepid, now even takes a couple of seconds longer to boot.

I've had this experience in the past - freshly installed systems would a lot boot faster, while upgrades would worsen the boot process. How come? How can my upgraded desktop benefit from those improvements?

---

### Post by BKonkle on 2009-04-28
I usually do a fresh install with each release to avoid issues like this.  I keep my /home folder on a separate partition, so all of my settings and files are preserved each time I upgrade.

When I installed Jaunty, I selected ext4 for all of my partitions.  I'm not sure how much of a boost the filesystem itself provides, but I know that my machines are booting in 20 to 25 seconds now with Jaunty.  Perhaps you should look into converting your partitions to ext4?  It's a rather unstable process though, so you may just be better off with a fresh install.

---

### Post by lodp on 2009-04-28
Yeah. Maybe I should just go with a fresh install. Would allow me to switch to ext4 and finally encrypt my system as well.

How much of a factor is ext4 in the shortening of the boot process in Jaunty anyway? And is it actually safe for deployment yet? I read there are a couple of bugs to be worked out.

I did choose ext4 on my laptop (which I use privately and where I'm less worried about data loss), and not only is the boot process now wicked fast, applications seem to load faster, too..

---

