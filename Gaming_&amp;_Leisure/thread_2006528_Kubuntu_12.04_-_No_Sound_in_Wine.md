---
title: "Kubuntu 12.04 - No Sound in Wine"
date: 2012-06-19
forum: Gaming &amp; Leisure
---

### Post by cottfcfan on 2012-06-19
I'm dual booting Kubuntu & Ubuntu 12.04, and using the stock install of Wine1.4.
On Ubuntu sound works fine, but on Kubuntu no sound.
I know its probably some dependency package thats being missed in Kubuntu, but anybody know which one?
Thanks.

---

### Post by cottfcfan on 2012-06-19
Ok, I found the missing dependencies for anyone else having this problem.

libasound2
libasound2 (i386)
libasound2-plugins
libasound2-plugins (i386)

ps. this was on kubuntu 64bit, 32bit may be ok.

---

