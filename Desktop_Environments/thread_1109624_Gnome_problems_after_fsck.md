---
title: "Gnome problems after fsck"
date: 2009-03-28
forum: Desktop Environments
---

### Post by mkartic on 2009-03-28
hey, i've been having trouble with my hard disk for a while now. after one of its recent attacks, i had to run fsck on my root and home partitions. now am not able to start gnome. i tried installing xubuntu, but doesn't work in that either. Am running fluxbox for now. Whenever i try opening firefox or nautilus, i get the following errors:

An error occurred while loading or saving configuration information for firefox. Some of your configuration settings may not work properly.

```
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Could not send message to gconf daemon: Message did not receive a reply (timeout by message bus))
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Could not send message to gconf daemon: Message did not receive a reply (timeout by message bus))
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Could not send message to gconf daemon: Message did not receive a reply (timeout by message bus))
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Could not send message to gconf daemon: Message did not receive a reply (timeout by message bus))
Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See http://www.gnome.org/projects/gconf/ for information. (Details -  1: Could not send message to gconf daemon: Message did not receive a reply (timeout by message bus))

```

am guessing its some gnome config files gone corrupt, any ideas how i should fix this?

PS: fluxbox feels kinda good :guitar:

---

### Post by inobe on 2009-03-29
did you unmount first ~~~~

---

