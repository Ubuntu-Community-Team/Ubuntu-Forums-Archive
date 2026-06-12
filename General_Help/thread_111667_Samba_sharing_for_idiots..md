---
title: "Samba sharing for idiots."
date: 2006-01-02
forum: General Help
---

### Post by radio1 on 2006-01-02
Well first, I'd like to say thanks to the forum. I have lurked and have learned a lot in the past few weeks that I have been playing with Ubuntu. To me, it is by far the best the best distro and Linux-only forum around.

Background:
For the past 6 weeks or so, I have fooling around with build a PVR box. First, a M$-based one- but I don't like the limited functionailty of it. Namely, I want to use my modded XBox as a front-end for the PVR-box. I have tried KnoppMyth... Easy to setup, but you can only really use the box for MythTV. It has a fluxbox desktop. I have installed KDE over it, but I do not like it. So, then, I discovered Ubuntu and a couple of HOWTOs on MythTV w/Ubuntu.

I really don't mind playing around and learning new things, and there is no real time-limit to this project, although 24 is starting up soon...

I'd like to access shared folders within a partition called /myth with 777 permissions (Ubuntu PVR-Box) from the XBox. I'll use XBMC and it's SAMBA support. (From the XBox- I know what to do.) My problem is the Ubuntu end.

What I got:
Ubuntu 5.10 Breezy installed.
static ip of 192.168.1.4
samba samba-doc smbclient smbfs swat winbind webmin installed.
3 Users:
1) Me (primary user)
2) MythTV (running backend- writes media to folders within /myth partition)
3) XBox (user setup)

I have all the tools but I am not sure how to put it all together. I know I have to set up some smb users, well, at least the one named XBox. How do I do that?

I know at least what I have to do, but I am not really clear on how even though I have read through many of threads here about such things.

For instance, I want to share /myth/videos at myip with user xbox. How would I got about doing this?

Help! (tia)

---

