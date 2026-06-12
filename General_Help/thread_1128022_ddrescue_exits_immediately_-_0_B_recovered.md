---
title: "ddrescue exits immediately - 0 B recovered"
date: 2009-04-17
forum: General Help
---

### Post by Al Grant on 2009-04-17
Hi Guys,

I am eager to learn about this tool, but my experience so far has been troublesome.

I am on Ubuntu and tried to copy some data from a disk with problems, this particular disks is recognised in windows and I can view it but parts of the disk are bad, so I expected ddrescue to at least copy parts of it.

Since I only have 20gig on my ubuntu box I have a SMB share with 200gig free that I use to out the image file on. My command line went something like:

sudo ddrescue -r 3 /dev/sdb /mnt/XonAl testlog

ddrescue starts but then immediately exits with all counters at 0 B.

I then wondered if I had done something wrong and ran the same command with the source as sdc (a 4 gig memory stick and it worked fine.

So I am note quite sure what I am doing wrong.

Any ideas????

sdb by the way is not mounted but does have a partition on it.

The data is not important its just a old disk I am playing around with for the purposes of learning ddrescue.

Cheers

-Al

---

