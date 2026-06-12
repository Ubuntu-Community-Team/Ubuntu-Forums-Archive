---
title: "marillat dependency problem w/ gstreamer"
date: 2005-05-25
forum: Desktop Environments
---

### Post by lee_connell on 2005-05-25
Hi all I'm using marillat unstable repos for gstreamer lame faad etc... and it's complaining that:

gstreamer0.8-faac:
  Depends: libc6 (>=2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed

How do i fix this?

---

### Post by Burgundavia on 2005-05-25
Please switch to the Ubutuforums backports hoary-extras.

The issue is that marilliat is tracking Sid, which has a new version of libc. 

Corey

---

