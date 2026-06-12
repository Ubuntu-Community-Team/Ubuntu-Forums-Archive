---
title: "APT times out on large updates"
date: 2005-12-12
forum: General Help
---

### Post by sile on 2005-12-12
I'm fairly new to Ubuntu, but I've been using Mandrake for a few years.  I just installed 5.10 on a clean box and everything seems just dandy except for the updates.  Whether through apt-get or through the GUI interface (whatever it's called), the download on updates over about 2MB or so always time out.  The smaller ones are just fine, it's only the larger ones that time out.  I'm pretty sure it's not a network issue, as we have 50Mbps fiber into the Time Warner network and have no issues downloading anything on any other workstations here.

Is this a known issue?  Thanks!

---

### Post by aysiu on 2005-12-14
It's not a known issue. Actually, this is the first I've heard of it.
Can you post the output of one of these large updates (sudo apt-get install whatever...)?

---

### Post by Gandalf on 2005-12-14
try editing your /etc/apt/sources.list and use another mirror to download from, don't forget to apt-get update afterwards

---

