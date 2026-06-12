---
title: "Ubuntu 8.04 VNC"
date: 2009-05-22
forum: General Help
---

### Post by rabbidlemming on 2009-05-22
I am attempting to setup an Ubuntu 8.04 machine for VNC.  I have some instructions setup by the previous admin of my area but it calls to edit the vncservers folder in the /etc/sysconfig.  The issue with this is that the sysconfig folder does not exist at all that I can find.

  I have tried the steps I found in some other threads to no avail.  Where can I insert the following lines so I can VNC into this machine?

VNCSERVERS:"1:username"
VNCSERVERARGS[1]="-geometry 1024X768 -depth 24 -alwaysshared"

Any help would be immensely appreciated as I have been slamming my head against this brick wall for almost two days trying to figure out what I'm supposed to do.

Signed,

  Lost in Ubunut 8.04

---

### Post by Kareeser on 2009-05-22
Unless I am mistaken, Ubuntu 8.04 should come with a VNC server preinstalled. You can access it through System -> Preferences -> Remote Desktop

---

### Post by rabbidlemming on 2009-05-22
Sometimes the simplest answers are the best ones, and this is the best. I can now VNC into this machine, thank you very much for your help.

---

