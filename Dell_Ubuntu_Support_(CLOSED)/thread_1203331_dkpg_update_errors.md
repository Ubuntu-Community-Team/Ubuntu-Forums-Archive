---
title: "dkpg update errors"
date: 2009-07-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Topazio785 on 2009-07-03
Hi,

I have been trying to apply update to my dell mini 12, ubuntu 8.04 and this is the message I am receiving

Preconfiguring packages...
dpkg: parse error, in file '/var/lib/dpkg/available' near line 2320 package 'gnome-settings-daemon':
 'Depends' field, reference to 'libgnome-2.0' : version contains ' "
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install. Trying to recover:


Any idea how I can solve this?

---

### Post by quixote on 2009-07-04
One common first step is to tell dpkg to fix all broken packages. ```
sudo dpkg --configure -a
```
If you've already tried that, I'm afraid I have no ideas about how to fix the specific error you mention. :(

---

