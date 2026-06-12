---
title: "iptables, or something else, blocking SAMBA?"
date: 2006-01-20
forum: Desktop Environments
---

### Post by nalmeth on 2006-01-20
Here is my home system (with roomates), with problem to follow

3 computers on WinXP
My computer with Breezy
a computer built with spare parts, on Breezy
2 Xbox's
2 routers delivering internet all over the house. 

We have an MSHOME system setup, which samba is supposed to interface with, and allow all connected computers to share/stream/view media. This works fine on my PC, and with the xbox's. I did not do any setup for this to work (as I can recall). It just worked out of the box.

The spare computer however, can't pick anything up. I have tried switching the router it's on, but it made no difference. I tried changing the router my PC was on aswell, and it worked on both, so I know it doesn't have to do with the 2 routers. 

I have checked the firestarter front-end to iptables, and have disabled it. No work.

What can anyone suppose is wrong here? Is there anyway an update (dist-upgrade, etc) could have changed some settings or permissions somewhere? Is it likely that iptables is blocking MSHOME somehow? How would I go about dealing with that?

Any other ideas?

---

### Post by ptmurphy on 2006-01-20
Try editing your smb.conf file and look to see if you have "security = user" in there somewhere.  If so, set it to "security = shared", reboot everything and see if the drive is visble.

I don't recommend you leave it this way, but it can help troubleshoot problems.

If that worked, set it back to "security = user" and make sure you 1) add a password for each user that you want to be able to login to a share (must be a valid ubuntu user, but is a separate password) using smbpasswd and 2) make sure you share the folders with proper permissions set.

---

### Post by nalmeth on 2006-01-20
hey, thanks for reply

changed *security = user* to *security = shared* but the MSHOME drive still did not appear.
To access the drive, I have been running in terminal:
nautilus smb:/
I've also been using smb4k, which I'm not very fond of...
Would it help if I posted my smb.conf?
What other samba browser would you recommend? I like how konqueror and nautlilus do it. I'd rather avoid mounting and unmounting drives all the time :D

---

