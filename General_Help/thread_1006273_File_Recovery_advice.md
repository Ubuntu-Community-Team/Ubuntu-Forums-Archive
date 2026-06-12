---
title: "File Recovery advice"
date: 2008-12-09
forum: General Help
---

### Post by leg on 2008-12-09
Let me start by saying that I have been a little silly and need some help to recover from it. 

It all started as I needed to get a usb stick prepared for a Debian install and followed some instructions I found on their install manual. Rather stupidly I copied verbatim one of the commands forgetting that my usb drive was mounted at a different point. This ruined my Ubuntu installation and I ended up re-installing. Actually that part of it was quite good and I ended up with 8.10 whereas I was on 8.04.

After re-installing all of my files are gone as /home wasn't seperate :( . Is there a method of recovering the files on that hard drive? Most of the stuff on there doesn't matter but there are some photos I would like to salvage if I can.

---

### Post by hyper_ch on 2008-12-09
don't you have backups?

---

### Post by leg on 2008-12-09
> **hyper_ch said:**
> don't you have backups?
Well I thought I did.

---

### Post by hyper_ch on 2008-12-09
so, first get another harddisk that is at least equal in size. Then make a dump onto that new harddisk using dd from a live cd.

```

sudo dd if=/dev/sda of=/dev/sdb

```
where /dev/sda is the original drive and /dev/sdb the new drive.

Then you unplug /dev/sda and you can start with some forensic tools (some people have mentioned photorec in this forum) and try to recover data. It's important to "use" the original harddisk as little as possible.

---

### Post by CrusaderAD on 2008-12-09
You could boot to a USB flash drive and browse the original file system. If it's been overwritten, it's gonna be a chore.

---

### Post by leg on 2008-12-09
Thanks both I will see how it goes.

---

