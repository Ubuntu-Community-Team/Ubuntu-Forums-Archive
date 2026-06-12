---
title: "Need help, switching over hard drives"
date: 2006-02-21
forum: Desktop Environments
---

### Post by Stelmate on 2006-02-21
I'm switching over to a new SATA drive from my old IDE.  How do my copy everything over so it is a mirror of my IDE? (I'm using 5.10) I don't have enough room to tar and untar everything so it would have to be a direct copy.

---

### Post by cskeide on 2006-02-21
Not long ago I found a [post]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/") explaing how to copy your /home directory. I've not tried this myself but it might work for your purpose.

1) mount your new partition at eg. /mnt/newdrive
2) cd /
3) find . -depth -print0 | cpio --null --sparse -pvd /mnt/newdrive/

---

### Post by Stelmate on 2006-02-22
Thanks,

It worked for my home directory (a couple of things were a little screwy from the transfer).  I definitely am too chicken to do it to the whole thing though.

---

### Post by cskeide on 2006-02-22
[QUOTE=Stelmate]Thanks,

It worked for my home directory (a couple of things were a little screwy from the transfer).  I definitely am too chicken to do it to the whole thing though.[/QUOTE]

Hehe. It's probably better to do a fresh install anyways. At least now you have a backup of your homedir =)

---

