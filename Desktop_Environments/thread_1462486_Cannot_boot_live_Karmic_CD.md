---
title: "Cannot boot live Karmic CD"
date: 2010-04-25
forum: Desktop Environments
---

### Post by astro4travel on 2010-04-25
Kind of an ongoing problem. When I insert the Live karmic CD it will load up to the point of starting X then the monitor shuts down into "out of range". I hear the loading music in the back round but no X or display. Now, I can load a live Knoppix CD just fine. It starts up and I have a display. I'm using an ATI-9600 graphics card. Not sure how to solve this!:confused:

---

### Post by tica vun on 2010-04-25
Does the .iso checksum match?

---

### Post by astro4travel on 2010-04-25
How do I check that?

---

### Post by astro4travel on 2010-04-28
I would like to check the xorg.conf file via the live cd. Should I let it load and then press ctr-alt-F1 to terminal and then should I type gksudo nautilus? And what are some of the things I should look for? Thanks in advance.

---

### Post by QIII on 2010-04-28
To check the downloaded .iso md5sum:

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If the hash does not match, re-download.

If it does, select the option to check the disk for errors when it boots.

If you have errors, it is likely an issue with the burn to CD.  Reburn it at the slowest possible speed your burning software will allow.

Let us know the results.

---

### Post by astro4travel on 2010-04-28
The CD was OK. No errors.  Thanks for the info.

---

### Post by astro4travel on 2010-04-30
I went ahead and downloaded the newest version on Ubuntu 10.4 Lucid and after I burned the CD and booted it up it did fine. Go figure!

---

