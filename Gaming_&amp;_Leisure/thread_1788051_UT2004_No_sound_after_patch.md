---
title: "UT2004 No sound after patch"
date: 2011-06-22
forum: Gaming &amp; Leisure
---

### Post by cheesekiller on 2011-06-22
I hadn't installed UT2k4 on Ubuntu before but i just got around to doing it. The sound worked if i used padsp (Ex. padsp ut2004) however after I updated the sound doesn't work with or without padsp...

---

### Post by MrMichaelHill on 2011-06-24
I'm in the same boat, been browsing the web and this forum for a few days now and nothing can seem to sort it! 

running 11.04 (64bit)

---

### Post by silex89 on 2011-06-25
I don't know what's going on either, I could play perfectly UT2004 in Ubuntu 9.10.... :(

---

### Post by Virus666 on 2011-06-25
If **padsp** does not work for you, you may try "**ALSA wrapper for OSS applications**." Install **alsa-oss** package via **Synaptic** and start the game with **aoss** command.

```
aoss ut2004
```

---

### Post by cheesekiller on 2011-06-26
```
aoss ut2004
ERROR: ld.so: object '/usr/lib/libaoss.so' from LD_PRELOAD cannot be preloaded: ignored.

```

idk if thats why but when i aoss it don't play sound either :(   got my hopes up though

---

### Post by Virus666 on 2011-06-27
The solution was provided in a near thread short time ago:

[http://ubuntuforums.org/showpost.php?p=10984049&postcount=5](http://ubuntuforums.org/showpost.php?p=10984049&postcount=5)

---

### Post by cheesekiller on 2011-06-27
your awesome, thats awesome, my game works now...   thank you so much

---

