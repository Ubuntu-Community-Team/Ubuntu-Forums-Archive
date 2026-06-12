---
title: "Getting Flashplayer 64-bit to work"
date: 2009-05-01
forum: General Help
---

### Post by cmnorton on 2009-05-01
I have downloaded the beta of Flashplayer 64-bit from Adobe. Basically, the zip file contains just the flashplayer shared object library, which I put out in the appropriate Firefox directory.  I am running 8.10, and kernel.log indicates there's been a seg fault

kern.log.0:Apr 26 12:41:45 hiawatha kernel: [  827.112416] npviewer.bin[10366]: segfault at 2c ip 00000000f6906af5 sp 00000000ffa567f0 error 4 in ibflashplayer.so[f68c0000+96d000]

Any ideas on what else I should try?

---

### Post by mb_webguy on 2009-05-01
Where did you put the Flash plugin, and did you make sure you've removed any other Flash plugins installed, as well as any remnants thereof?

---

### Post by Paqman on 2009-05-01
> **cmnorton said:**
> 
Any ideas on what else I should try?

Re-download? You don't need to do anything to get it to work. Just put that file in the plugins directory.

---

### Post by oldos2er on 2009-05-01
Try the script here: [http://home.comcast.net/~ubuntume/Get64bitFlash-0.1.tar.gz](http://home.comcast.net/~ubuntume/Get64bitFlash-0.1.tar.gz)

---

### Post by soro2005 on 2009-05-01
> **cmnorton said:**
> kern.log.0:Apr 26 12:41:45 hiawatha kernel: [  827.112416] npviewer.bin[10366]: segfault at 2c ip 00000000f6906af5 sp 00000000ffa567f0 error 4 in ibflashplayer.so[f68c0000+96d000]

Should be libflashplayer.so, not ibflashplayer.so, shouldn't it? :confused:

---

### Post by cmnorton on 2009-05-02
> **soro2005 said:**
> Should be libflashplayer.so, not ibflashplayer.so, shouldn't it? :confused:

As to ibflashplayer, you're right. It's a typo.

I fixed the problem by re-installing the original Flash Player.

---

