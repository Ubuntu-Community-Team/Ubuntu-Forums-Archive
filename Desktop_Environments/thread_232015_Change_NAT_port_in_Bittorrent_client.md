---
title: "Change NAT port in Bittorrent client"
date: 2006-08-08
forum: Desktop Environments
---

### Post by finite9 on 2006-08-08
How do I change the port to be used in the official bittorrent client?  I have set it on my router to a non-standard port but do not know how to change it in bittorrent.

--finite9

---

### Post by nomizzz on 2008-05-10
I have this same question (2 years later).  I'm running Hardy Heron 8.04 and I need to change the port because all the trackers I'm downloading from block port 6881.

I know there's some command line option like -minport 10000 --maxport 10100, but what's the actual command?

---

### Post by finite9 on 2008-05-12
you need to edit the startup program for bittorrent and add --minport --maxport to the command line.

---

