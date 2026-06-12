---
title: "Looking for a hard disk copy tool"
date: 2009-02-05
forum: General Help
---

### Post by Goombie on 2009-02-05
I'm thinking of upgrading to a bigger hard drive for my laptop (I never thought 80GB would be too small, but it is), and I was wondering if there was a good program out there that could copy everything on my old hard drive - OSes, partitions, MBR, etc - onto the new hard disk. Basically, I'm looking for something to make a bit-for-bit copy of the contents of my old hard drive onto my new one. What does the all-powerful forum community have to say?
;)

---

### Post by Locutus_of_Borg on 2009-02-05
```
dd if=/dev/sda of=/dev/sdb
```

change sda to whatever the hard drive label of your current drive is, and sdb to whatever the new drive is, do this from a livecd as root, and be prepared to wait a long time


you could also try something like partimage but dd is much more through

---

### Post by HermanAB on 2009-02-05
Hmm, dd of course:
[http://aeronetworks.ca/netcat-howto.html](http://aeronetworks.ca/netcat-howto.html)

Cheers,

Herman

---

### Post by dcstar on 2009-02-05
> **Goombie said:**
> I'm thinking of upgrading to a bigger hard drive for my laptop (I never thought 80GB would be too small, but it is), and I was wondering if there was a good program out there that could copy everything on my old hard drive - OSes, partitions, MBR, etc - onto the new hard disk. Basically, I'm looking for something to make a bit-for-bit copy of the contents of my old hard drive onto my new one. What does the all-powerful forum community have to say?
;)

You don't want to "dd" from one drive to a bigger one because the small drive partition table (containing the size of the original drive) may well be copied across - and this can cause trouble later.

You can use a Live CD and the Partition Editor to copy individual partitions, and then just reinstall grub onto the new disk using the instructions you can search out in the forums.

Then you should end up with a drive that boots up, knows it is a big drive and has all your old stuff on it exactly as before.

---

