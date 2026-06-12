---
title: "Real Player"
date: 2005-11-17
forum: Desktop Environments
---

### Post by vxj9219 on 2005-11-17
I downloaded and installed Ubuntu today. Later I installed RealPlayer according to instructions here:

[http://jroller.com/page/triplem74?entry=ubuntu_breezy_badger_and_realplayer](http://jroller.com/page/triplem74?entry=ubuntu_breezy_badger_and_realplayer)

when i type realplay in the terminal, realplayer wont open. i then tried clicking on realplay.bin, still it wont open. how can i fix this thing?

---

### Post by arnieboy on 2005-11-17
[QUOTE=vxj9219]I downloaded and installed Ubuntu today. Later I installed RealPlayer according to instructions here:

[http://jroller.com/page/triplem74?entry=ubuntu_breezy_badger_and_realplayer](http://jroller.com/page/triplem74?entry=ubuntu_breezy_badger_and_realplayer)

when i type realplay in the terminal, realplayer wont open. i then tried clicking on realplay.bin, still it wont open. how can i fix this thing?[/QUOTE]
the easiest way to install real player 10 is the following:
```
sudo gedit /etc/apt/sources.list

```add the following line to the end:
[PHP]deb http://public.planetmirror.com/pub/plf/ubuntu/plf/ breezy free non-free[/PHP]
save and close the file.
then do:
```
sudo apt-get update
```
```
sudo apt-get install realplay
```
that will get u all set. look for realplayer 10 in applications--> sound and video

---

### Post by vxj9219 on 2005-11-17
thanks man. that worked.

---

