---
title: "samba mount not robust enough"
date: 2006-03-19
forum: Desktop Environments
---

### Post by bmgz on 2006-03-19
*** sorry server timed-out during my first post ***

I have numurous windows/ubuntu clients, so I just use Samba for all of them.
I was using Samba and NFS but NFS permissions became a nightmare.
I mount a share on all the clients during boot via an fstab entry.

My only problem is if my server reboots or I restart the Samba service on the server (slackware 9.1), all the ubuntu clients just start hanging indefinately.

I have to actually totally reboot them. Is their a way to make a samba mount as robust as NFS?

---

