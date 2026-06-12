---
title: "no sound etqw"
date: 2007-10-26
forum: Gaming &amp; Leisure
---

### Post by mbradlcu on 2007-10-26
Hi folks,
yesterday I had sound playing the full version of etqw with the native Linux client, and tonight there was no sound,, ??? I didn't change anything! nadda,, zip ,, you get the idea,, any way the fix for me was to alter the ~/.etqwcl/base/etqwconfig.cfg file and change: 
seta s_driver "alsa"
to
seta s_driver "oss"

if anyone would like to offer a proper fix that would be great! but until then I hope this helps someone..

---

### Post by AnRkey on 2007-11-18
This worked for me, thanks very much!

---

### Post by jebblue on 2010-06-05
It worked for me too after upgrading to 10.04, thanks!

---

