---
title: "How to add new hard drive?"
date: 2006-09-18
forum: Desktop Environments
---

### Post by kuririkura on 2006-09-18
How to add new hard drive as a root partition?

My Ubuntu hard drive only had some space left, i want to add new hard drive as part of the root/var/usr , Anyone can help me?

regards,
Eka

---

### Post by WalmartSniperLX on 2006-09-18
It should be 'plug n play'. Just plug it in and it should detect it as a storage device. Make sure its formatted correctly for linux. I prefer fat32 for a storage device or you can do ext3.

Im not sure, but see if you can format it in ubuntu.

EDIT: like i said im not sure lol, read the post below mine :D thanks for making your post

---

### Post by aysiu on 2006-09-18
I don't think you can add a new drive as /

You can easily add one as /var or /usr, though.

Here's a tutorial on making a separate /home partition. I think the same principles apply for /var and /usr:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by snakyjake on 2006-09-18
Here's the basics:
1. Create a new partion on your new hard drive.
2. Mount the new partition to the mount poing /var/usr.

But, your previous data (if there was any) won't be in /var/usr.  So before you mount in step #2, you need to move your data out of the directory and into a new/temporary directory.  Then mount the new partition, and then move your data to /var/usr on your new drive.

Jake

---

