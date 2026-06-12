---
title: "Working with nautilus -- warning GConf error"
date: 2009-01-04
forum: Desktop Environments
---

### Post by cigtoxdoc on 2009-01-04
I have my PC setup so that there are two users: 1) dad (myself and administrator); and 2) son (my preteen Son).

While he was working with the PC, one of our cats ran into the power cord and the PC crashed.  He was working on a presentation in OOo 3 Presentation.

He restarted the PC and logged in as son.  He then went to work on one of his presentations and got an error saying "cannot save filename:"

I then opened a terminal window, logged in as root, and ran nautilus.  I got the following warning:

son@dad-desktop:~$ su
Password: 
root@john-desktop:/home/son# nautilus

(nautilus:7532): GnomeUI-WARNING **: While connecting to session manager:
None of the authentication protocols specified are supported.

(nautilus:7532): Eel-WARNING **: GConf error:
  Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)

What does above warning mean?

John

---

