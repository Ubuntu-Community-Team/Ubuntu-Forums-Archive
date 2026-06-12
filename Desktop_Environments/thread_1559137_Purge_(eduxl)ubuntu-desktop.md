---
title: "Purge (edu/x/l)ubuntu-desktop"
date: 2010-08-23
forum: Desktop Environments
---

### Post by rykel on 2010-08-23
Hi,

How do I purge ALL programs there were installed with xubuntu-desktop, lubuntu-desktop and edubuntu-desktop?

I installed them using apt-get so using aptitude to remove their associated packages do NOT work.

Thank you.

---

### Post by XubuRoxMySox on 2010-08-23
Try selecting the one(s) you want to remove in Synaptic (Mark for Complete Removal). Before you click Apply, look over the list of stuff "To Be Removed," including "To Be Completely Removed including config files") and make sure that's what you want to happen. If it is, click Apply and Synaptic should do it all automagically!

Let us know....

-Robin

---

### Post by rykel on 2010-08-23
Thank you Robin, but that is not what I am looking for...

I am literally looking for a list of ALL packages that get pulled in when we do a, for example, "sudo apt-get install edubuntu-desktop".

Something like what Aysius has done before... "sudo apt-get remove edubuntu-desktop edubuntu-this edubuntu-that program-this program-that..."

The reason why your answer does not work is that by selecting, eg. edubuntu-desktop, it only removes "edubuntu-desktop" the meta-package itself. It does NOT remove any other programs/files.

---

