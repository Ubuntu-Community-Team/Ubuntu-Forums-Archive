---
title: "Kaffeine deactivates DMA in CDROM drive"
date: 2005-11-22
forum: Desktop Environments
---

### Post by hil on 2005-11-22
I tested my DVD on both Kaffeine and xine. Kaffeine deactivated the DMA of the CDROM drive every first time I ran it after boot. I re-activated my DMA and it worked fine in Kaffeine. xine did not have that problem. Check after you start Kaffeine. DMA might be deactivated. Here is the procedure:

Boot Kubuntu 5.10
After KDE finishes starting, activate the DMA by doing ```
sudo hdparm -d1 -X66 /dev/hdc
```
Insert the DVD disc. Kaffeine should automatically start to play.
Check the DMA by doing ```
sudo hdparm /dev/hdc
```
DMA is deactivated by Kaffeine.

---

### Post by magicfab on 2005-11-22
This seems to be related specifically to Kaffeine. I would suggest you enter a bug report here:
[http://bugzilla.ubuntu.com/enter_bug.cgi](http://bugzilla.ubuntu.com/enter_bug.cgi)

Make sure the word "Kaffeine" and "DMA" are in the description of the bug. There seems to be lots of Kaffeine bugs, though.

---

### Post by alvonsius on 2005-11-22
Humm ... i always enabling DMA on DVD using driver /dev/dvd and it runs ok ... are /dev/hdc and /dev/dvd are the same??? Sorry for adding another question ... I'm just a curious guys here :D

---

### Post by hil on 2005-11-22
In my laptop, /dev/dvd points to /dev/hdc
```
h@t30:~$ ls -Al /dev/dvd
lrwxrwxrwx  1 root root 3 2005-11-22 01:48 /dev/dvd -> hdc
h@t30:~$
```
How many of you have this problem too?

---

