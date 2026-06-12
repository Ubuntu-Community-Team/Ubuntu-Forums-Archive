---
title: "Updating Ubuntu Dapper-based MythTV box"
date: 2006-08-31
forum: Desktop Environments
---

### Post by manoova on 2006-08-31
I have a MythTV box running Ubuntu Dapper. Everything is working perfectly. It's now reporting that it wants to update various components including linux-image-2.6.15.

To install the IVTV drivers you are prompted to do the following:

> apt-get install linux-source-<kver> linux-headers-`uname -r`

and then

> tar xvjf /usr/src/linux-source-*.tar.bz2 -C /usr/src/
ln -s /usr/src/linux-source-<kver> /usr/src/linux
ln -s /usr/src/linux /lib/modules/`uname -r`/build

What I would like to know is this: Will updating my Ubuntu Dapper installation break anything at the kernel level if I have compiled in the IVTV module?

I'm really hesitant to upgrade if it will render my MythTV box useless.

Thanks.

---

### Post by MetalMusicAddict on 2006-08-31
I think it will. I think you will have to re-do the IVTV drivers. On a side note, What is you MythTV system made up with? MiniITX? How hard was MythTV to setup?

---

### Post by manoova on 2006-08-31
That's what I feared. To be honest it's not too hard to redo the ivtv drivers. As for installing MythTV, it can be quite tough but after the millionth time installing it it gets much easier!

My hardware setup is nothing fancy: 1.7Ghz Intel P4 with 512Mb Ram and a 300Gb HDD. Using a Hauppauge 350 card. I've connected the MythTV box to my Sky satellite decoder which I am controlling with a SkyControl box.

I wrote a howto which you can grab here.

---

### Post by MetalMusicAddict on 2006-08-31
Thanx sir. REALLY nice How-To. I plan on putting all the back-end stuff on my server (has the PVR-250) and have a client control the recording via Myth-Web.

Just gotta get SPDIF working right on my HTPC. ;)

---

### Post by elmatador6667 on 2006-08-31
Thx Manoova you're brilliant.

---

### Post by Titus A Duxass on 2006-08-31
If it ain't broke don't fix it.

I was in the same situation as you, I updated and everything was hosed.

Disable the updating in the adept manager and leave alone.

---

