---
title: "gdm face browser global pixmaps doesn't work"
date: 2010-10-29
forum: Desktop Environments
---

### Post by psyke on 2010-10-29
I have a NFS mounted home dir, so i couldn't use .face for the users in the gdm Face Browser. In older Ubuntu versions I would have just put the images in /usr/share/pixmaps/faces/ and it worked.

For some reason that doesn't work any more.
Can't tell you which was the last version it worked on, but i will try to find out and post later!

right now I use Ubuntu 10.10 with gdm 2.30.5

tried: jpg, png and username without extension
also tried: /usr/local/share/pixmaps/faces/
and to configure it in /etc/gdm/custom.conf

couldn't find anything online,
regarding the gdm doc for 2.30 it still should work that way!

---

### Post by psyke on 2010-11-08
found another solution!
gdm is caching the faces in /var/cache/gdm/*username*/face

just put them all there! :)

---

