---
title: "Update Manager Error after fresh install"
date: 2011-01-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by tekkman on 2011-01-19
Hey guys, Im trying to update my dell laptop after a fresh install of Ubuntu, but the error it gives me is below.

"Not enough free disk space

The upgrade needs a total of 507M free space on disk '/'. Please free at least an additional 238M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'."

Im 100% sure I have more than 254.9GB left on my hardrive considering it's a 2-3 month old laptop.
So I did what it told me, and still that message, so I thought I'd hand it to the community, thanks!

Also the error is below!

---

### Post by wilee-nilee on 2011-01-20
Boot the Live Ubuntu cd, go to system-admin-gparted. Open gparted and take a screenshot and post it.

---

### Post by tekkman on 2011-01-20
I can't seem to find that, and Im running Ubuntu 10.10 Desktop Edition, I ordered it.

---

### Post by wilee-nilee on 2011-01-20
> **tekkman said:**
> I can't seem to find that, and Im running Ubuntu 10.10 Desktop Edition, I ordered it.

So what I'm trying to find out is what operating systems are on the computer, how many partitions there are, and how big they are. Run this in the Ubuntu terminal and post the text. :)
sudo fdisk -lu

---

### Post by tekkman on 2011-01-20
Never mind, I re-installed Ubuntu, and noticed that the installation size I put was 3GB, so I re-installed it with the default which was 17GB :)

---

### Post by wilee-nilee on 2011-01-20
> **tekkman said:**
> Never mind, I re-installed Ubuntu, and noticed that the installation size I put was 3GB, so I re-installed it with the default which was 17GB :)

Good, so it sounds like a wubi install, if so make sure you mention that if you have any problems.

---

