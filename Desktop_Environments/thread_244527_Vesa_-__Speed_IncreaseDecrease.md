---
title: "Vesa -  Speed Increase/Decrease?"
date: 2006-08-26
forum: Desktop Environments
---

### Post by OzzOzzOzz on 2006-08-26
Hey All

Just installed ubuntu and starting to enjoy it, but I have
a few problems to sort out.

Ubuntu is much more sluggish than XP was on this same computer.
It is a P4 3.00Ghz HT 512Mb Ram. 

I read some advice about installing the 686-smp kernel which 
I have done, and Ubuntu now correctly recognises two CPU's.

The problem is, it still seems sluggish when moving or maximising/minimising
windows. Apparently, this may be due to the generic graphics driver.

I am using a Asus P5S800-VM motherboard with the integrated graphics card (SIS AGP I think).

Does anybody know of a driver which I could use for this? or and driver that is better than the standard one? (The asus website turned out blank)

Is there anything else I can do to get rid of this sluggishness?

Thanks All.

Cheers
Ozz

---

### Post by OzzOzzOzz on 2006-08-26
Changed XConf to use the 'sis' driver.

Most of the 'choppyness' seems to have gone away.

Any other performance tweeks?

---

### Post by Ramses de Norre on 2006-08-26
When I used metacity I used to set the reduced_resources option, to do so: ```
gconf-editor /apps/metacity/general
```
[This]("http://www.ubuntuforums.org/showthread.php?t=179540") and [this]("https://help.ubuntu.com/community/WebBrowsingSlowIPv6IPv4") (Dapper part!) are also a must for a new ubuntu install.
For more tweakings: use the system and browse the forums ;)

---

### Post by OzzOzzOzz on 2006-08-26
Thanks, will try that and let you know.

---

