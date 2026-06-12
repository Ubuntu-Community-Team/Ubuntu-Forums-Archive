---
title: "install xubuntu-desktop package from xubuntu.iso ?"
date: 2009-03-08
forum: Desktop Environments
---

### Post by S.A.A on 2009-03-08
Hi, i have ubuntu intrepid installed on an offline desktop, so i want to install xubuntu-desktop package from an xubuntu cd, is that possible ?

---

### Post by ugm6hr on 2009-03-08
Only if the CD is the AlternateCD.

---

### Post by S.A.A on 2009-03-08
could you please say HOW ?

---

### Post by ugm6hr on 2009-03-08
Try putting the CD into the drive.

It should allow you to add the CD as a software source.

Then install as usual.

Are you intending to download the CD specifically for this?

---

### Post by S.A.A on 2009-03-08
yes im doing that right now, is that wrong ?

---

### Post by ugm6hr on 2009-03-08
There may be an easier (and better) way.

Do you have access to the internet from any Ubuntu machine (even narrow-band)?

---

### Post by S.A.A on 2009-03-08
Yes, what's your idea ?

---

### Post by ugm6hr on 2009-03-08
> **S.A.A said:**
> Yes, what's your idea ?

Either:

1. Use *apt-get install -d xubuntu-desktop* to download all packages to a different computer (assuming same Ubuntu version - inc 32 - vs - 64 bit) and just copy /var/cache/apt/archives to offline computer.

2. Use Synaptic to "Generate package download script" (in File menu).  Then use script on broadband computer (uses wget).

Benefits:
Get latest packages
Smaller download

---

### Post by S.A.A on 2009-03-08
This is great, thank you.
i will definitly try this, again thank you for listning.

---

