---
title: "Can't move Windows Thunderbird files over"
date: 2008-12-11
forum: General Help
---

### Post by thegizmoguy on 2008-12-11
Hi everyone!  So I've been trying to move my Thunderbird profile directory from my NTFS windows XP partition to my .mozilla-thundirbird except every time I try to copy off all the files I get "Permission denied".  Why can't I do this?

---

### Post by quibbler on 2008-12-12
> **thegizmoguy said:**
> Hi everyone!  So I've been trying to move my Thunderbird profile directory from my NTFS windows XP partition to my .mozilla-thundirbird except every time I try to copy off all the files I get "Permission denied".  Why can't I do this?
You probably need to be root. Open a terminal and type

gksudo natilus

This will open Nautilus as root, then select and copy the files where you want.

Regards quibbler

---

### Post by quibbler on 2008-12-12
> **thegizmoguy said:**
> Hi everyone!  So I've been trying to move my Thunderbird profile directory from my NTFS windows XP partition to my .mozilla-thundirbird except every time I try to copy off all the files I get "Permission denied".  Why can't I do this?
You probably need to be root. Open a terminal and type

gksudo natilus

This will open Nautilus as root, then select and copy the files where you want.

Regards quibbler

---

