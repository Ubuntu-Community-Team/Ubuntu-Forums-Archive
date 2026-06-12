---
title: "Adding applications from Debian CD's"
date: 2005-02-17
forum: Desktop Environments
---

### Post by thane on 2005-02-17
:?:  Hi,

I am on a 56k modem at home but can download Debian CD's at work (I currently have copies of Sarge). How much of a problem would I be causing myself to add these to my apt/sources to get all of the docbook and tetex tools I need to use and create documents with Ubuntu?

I would rather not try to down load it via the Internet; i.e., 40+ megabytes of software over a connection that feels like trying to suck a milkshake through a coffee straw.

---

### Post by rkn on 2005-02-17
This works ok for me.  I have broadband at work and dial-up at home.
# apt-cdrom add
to add a CD to your sources list.   90% of testing and unstable progs are the same version numbers, but you may run into a prog now & then that dosen't match up with your installed library versions.


Bob

---

