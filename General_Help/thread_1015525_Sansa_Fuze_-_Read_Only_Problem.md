---
title: "Sansa Fuze - Read Only Problem"
date: 2008-12-18
forum: General Help
---

### Post by SlalomMan on 2008-12-18
I just did a clean install of Intrepid after using Feisty, Gusty, and Hardy for quite some time. I got a Sansa Fuze this summer, and I learned all about using it with linux (.is_audio_player, etc) to get it working with Rhythmbox. Now I have a problem; when I try to transfer music onto it, I get a "directory is read only" error. I think it's got something to do with the mount options that are there...because "ro" is on the bunch. I think I should try and put "rw" or "rw+" or something similar, but last time I messed with mount options, it screwed up my SD card for a bit.

My "file system" options are as follows: ro nosuid uid=1000 fmask=0077

My Mount options are: dmask=0077 codepage=cp437 iocharset=iso8859-1 shortname=mixed utf8 flush

I don't know how to make changes to the settings there; I would assume it would have something to do with fstab or mtab, but mtab is only temporary stuff, so I can't edit that, right?

Any help is appreciated.

---

### Post by tv0571 on 2009-02-14
SLalomMan, did you get it working?

I have a similar problem with my Fuze.   I see these same mount options in (Menu) Places / Computer / <Sansa Fuze> ; right click properties / Volume Tabe / Settings -- you have the option to change some volume settings. Maybe the ro there is causing the problem.

---

### Post by tv0571 on 2009-02-14
OK, so I took the chance of changing the ro to rw and now not only will it not mount but it won't pull up the tabs to let me change it back.  I found some .xml under ./gconf/system/storage/volumes that showed my recent change - so I removed that, but still I get no mount.  Ugh.

---

