---
title: "Inspiron 1526 &amp; Hardy: Wireless not recognized"
date: 2008-05-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jmwyatt on 2008-05-18
New 1526. Clean install Hardy. I have both stock Dell card and Intel card... Neither are recognized (no-show lspci). Reinstalled OS, updated/upgraded, used backports, tried solutions peppered around forum, etc. No avail. Any ideas?

---

### Post by shoreline on 2008-05-18
I got my wireless Broadcom 4310 (rev 01) card working on Dell Inspiron 1525 + Hardy Heron.

This is the comprehensive guide that used: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

I understand that Dell's wireless cards are based on Broadcom chips, so this might work for you. But you need to know the make of your card. Check the output of lspci for that !

Good luck !

---

### Post by JKBurton on 2008-05-20
> **shoreline said:**
> I got my wireless Broadcom 4310 (rev 01) card working on Dell Inspiron 1525 + Hardy Heron.

This is the comprehensive guide that used: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)


I looked in several different threads, downloaded drivers from different sites and following different procedures. This is the one that worked on my own 1526. Step 2e, to be specific.

Do note that if you've tried other drivers first, you need to "ndiswrapper -l" and "sudo ndiswrapper -r <drivername>" to uninstall each bad one you've installed, before trying a new one.

Thanks, shoreline!

---

### Post by jmwyatt on 2008-05-25
If lspci shows no device. How should I proceed?

---

### Post by shoreline on 2008-05-26
JWyatt, post the output of:

```
sudo lspci
```

and

```
sudo lshw
```

---

### Post by jmwyatt on 2008-06-14
Thanks, all. Got it! (using info from JKBurton?Shoreline post)

---

