---
title: "&quot;no such partition&quot;-error after upgrading kernel"
date: 2009-01-11
forum: General Help
---

### Post by larsgj on 2009-01-11
Summary:
Using winXPSP2, Ubuntu 8.04 on hard disk with only one partiton. The hard disk is physical drive # 3.

After kernel update via synaptic the menu.lst was changed. Idiot me chose change to new believing that it was just the usual 
(hd0,0) that should be changed to (hd3,0).

But after restart error 22 "no such partiton" appeared. I have tried different combinations of (hdx,y) and I have tried entering (hd3,0)/ubuntu/disks/root.disk instead of just (hd3,0)/ubuntu/disks

- with some changes I get a file not found error... but menu.lst is in the mounted "file-disk" is it not? so when the system can read that - it should work...shouldn't it?

Help appreciated :) 

best regards - Lars

---

