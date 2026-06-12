---
title: "Cannot Eject DVD  - evince-thumbnailer blocks eject"
date: 2009-06-19
forum: General Help
---

### Post by BenUrsa on 2009-06-19
evince-thumbnailer locks DVD and prevents ejecting DVD

Example (DVD is a Data Disk, my backups from March).

Right click the disks desktop icon and select eject and you get an error box with the message:

An application is preventing the volume 'Backups29Mar2009' from being unmounted.

Press the drives eject button and you get (after about a minute) this error message:

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.


In a terminal window
$ lsof | grep cdrom
evince-th 31559       bear    6u      REG       11,0   213641    1635 /media/cdrom0/tigergps.pdf
$ kill 31559

Now you can eject the DVD.

Suggestions appreciated.  It appears to be a bug in evince-thumbnailer.

My system is a DELL Inspiron 9300 2.6.28-11-generic #42-Ubuntu SMP.

The problem does not happen on all DVD.  It appears to be pdf files that cause the hangup.

Suggestions?  Ben Ursa

---

