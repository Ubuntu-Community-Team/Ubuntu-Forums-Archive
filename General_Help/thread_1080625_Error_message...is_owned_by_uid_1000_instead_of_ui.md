---
title: "Error message...is owned by uid 1000 instead of uid 0"
date: 2009-02-25
forum: General Help
---

### Post by ozguitarplayer on 2009-02-25
I get this message occasionally when using terminal, the first part is often different however the...is owned by uid 1000 instead of uid 0.....is always the same

Error: "/var/tmp/kdecache-nigel" is owned by uid 1000 instead of uid 0.  

What does it mean and how can I correct it?
Any suggestions?

---

### Post by bodhi.zazen on 2009-02-25
Hard to know exactly, common issues would be :

1. You changed the permissions of system files.

2. You are running graphical applications as root without using kdesu (ie sudo kate rather then kdesu kate).

If it is a single file you can try 

```
sudo chown root.root /var/tmp/kdecache-nigel
```

---

### Post by ozguitarplayer on 2009-02-25
thanks bodhi.zazen
It's multiple files...can it be corrected?

---

### Post by bodhi.zazen on 2009-02-25
Multiple files in /tmp or multiple files across your system such as /etc and /usr and /var ???

---

### Post by ozguitarplayer on 2009-02-25
seems to be mostly /tmp and /var

Error: "/tmp/ksocket-nigel" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-nigel" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-nigel" is owned by uid 1000 instead of uid 0.
kdeinit4: preparing to launch /usr/bin/kbuildsycoca4
kbuildsycoca4 running...
Error: "/var/tmp/kdecache-nigel" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-nigel" is owned by uid 1000 instead of uid 0.


hope this helps

---

### Post by djsephiroth on 2009-03-02
D'oh! Looks like I should run kdesu instead of sudoing all over my Kubuntu install. This explains a lot. XD Thanks for resolving this.

---

### Post by 0zcan on 2009-11-18
Tried the above with Mint 7 64 bit - initially the sudoing worked but couple of minutes later my system would not respond. Either this command broke it or something on my system made is highly unstable and thus locking up.

I finally had to press the reset button.

Thanks for the folks above!

---

