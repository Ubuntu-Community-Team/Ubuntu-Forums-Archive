---
title: "dpkg: error processing linux-restricted-modules-generic"
date: 2009-03-08
forum: General Help
---

### Post by rokky on 2009-03-08
For Ubuntu 8.04:

I had the subject message pop up today when I tried to install this as a pre-requisite for something that goes with the "Gnome Do" package (based on a nifty article by Kyle Rankin in Linux Journal).  The full text is:

 Package linux-restricted-modules-2.6.24-24-generic is not configured yet.
dpkg: error processing linux-restricted-modules-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.24.24.26); however:
  Package linux-image-generic is not configured yet.


After that I started having problems with automounting of USB flash drives - getting popups that the directory in /media cannot be created for the mount point even after changing ownership of /media to the Id I normally use for these operations.  Since it seemed the automounter/hal/plugdev nexus got hosed, I tried to install pmount to see if that would help (based on a thread about using that for automount problems), but got the same errors about the unconfigured restricted modules again.  

This is looking as though the root cause goes back to my packages database being messed up now, and I have to believe the partial update for Gnome Do that hung on the generic restricted modules and being in an unconfigured state is involved.

Any ideas or known problems with this restricted modules dpkg issue that may have just cropped up in the last few days (I did a fairly normal update for whatever came along a few days ago - think it was a Firefox 3 security update - could it go back to that?)?

TIA
R

---

