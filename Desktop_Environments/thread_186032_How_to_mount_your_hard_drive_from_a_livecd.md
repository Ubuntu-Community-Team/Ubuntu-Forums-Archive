---
title: "How to mount your hard drive from a livecd"
date: 2006-06-01
forum: Desktop Environments
---

### Post by beforewisdom on 2006-06-01
Wow, am I ever so glad I replied back with this answer after I figured out a problem on my own.

In the process of upgrading to dapper my x configuration got messed up.   Since I have cable I can get on the internet via the livecd to ask for help.   I can also see my hard drive from the livecd with these commands.  I am posting these here because I am sure it will come in handy and I remember it being hard to find how to do this on google:

sudo bash
cd /mnt
mkdir /mnt/myharddrive
mnt /dev/hda1 /mnt/myharddrive

Your hard drive might not be "hda1"

Good Luck

Steve

---

### Post by altonbr on 2007-03-13
"mnt" isn't a program...

---

