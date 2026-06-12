---
title: "x201t Tablet Keys not recongized by xev"
date: 2010-07-09
forum: Desktop Environments
---

### Post by mweinelt on 2010-07-09
Hi there,

I got my self an x201 Tablet as of last week. Everything works out fine, like tablet, fingerprint, webcam and stuff - only the tablet keys are not beeing recognized by xev itself. Needless to say I can't bind them to a certain command, which makes working in Tablet-Only mode needlessly cruel.

Any ideas on how to figure this out?

Answers appreciated, thanks in advance.

---

### Post by mweinelt on 2010-07-16
bump

- xev failed me
- showkey -s (as root) failed me
- randomly catting /dev/input/* and waiting for a reaction failed me
- can't find any acpi event either

I'm screwed :/

---

### Post by mweinelt on 2010-07-22
Bump

---

### Post by Favux on 2010-07-22
Hi mweinelt,

I can't answer your question directly.  But maybe something in these links can help.

I'm sure your aware of the thinkwiki but just in case:  [http://www.thinkwiki.org/wiki/Installing_Ubuntu_9.10_(Karmic_Koala)_on_a_ThinkPad_X200](http://www.thinkwiki.org/wiki/Installing_Ubuntu_9.10_(Karmic_Koala)_on_a_ThinkPad_X200)
which links to:  [https://help.ubuntu.com/community/X61T](https://help.ubuntu.com/community/X61T)
and the Thinkpad acpi:  [http://www.thinkwiki.org/wiki/Thinkpad-acpi](http://www.thinkwiki.org/wiki/Thinkpad-acpi)
also:  [http://www.thinkwiki.org/wiki/How_to_get_special_keys_to_work](http://www.thinkwiki.org/wiki/How_to_get_special_keys_to_work)

It's possible the thinkpad uses a wmi acpi bios extension.  It would be called something like ibm-wmi.  I think I may have seen something like that.

---

