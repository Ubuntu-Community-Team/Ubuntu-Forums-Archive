---
title: "ZSNES 1.42: Sound is crackly, distorted, and out of sync..."
date: 2006-07-06
forum: Gaming &amp; Leisure
---

### Post by sktx on 2006-07-06
i've tried everything to fix this, and can't find a solution on google, forums or wiki.  i've tried multiple combinations of audio setting to try and get this to work, and even downloaded, configured, compiled and installed the source using checkinstall.  

but STILL, the audio is crackly and out of sync.  this only started happening after i upgraded to dapper from breezy using the alternative CD. 

anyone have any ideas?

  ::sktx::

---

### Post by vampiric_blade on 2006-07-09
Remove libdsl1.2debian-alsa with apt and install libdsl1.2debian-oss.  This will take care of the problem.

---

### Post by hygraed on 2006-07-09
> **vampiric_blade said:**
> Remove libdsl1.2debian-alsa with apt and install libdsl1.2debian-oss.  This will take care of the problem.

Can you give us the exact commands? (I've been having the same problem.)

---

### Post by jISh on 2006-07-09
apt-get remove libdsl1.2debian-alsa
apt-get install libdsl1.2debian-oss

Werd.

---

### Post by DanielSmith604 on 2007-02-06
I believe you mean libsdl :)

Using nUbuntu on a toshiba laptop. Fixed the sound problem. Youtube streaming video and quake sounded fine too. Thanks

Rock on!

:guitar:

---

### Post by indros on 2007-03-09
This worked perfectly for me as well.  Thank you! :) 

ZSNES 1.42
Ubuntu 6.10 Edgy

---

