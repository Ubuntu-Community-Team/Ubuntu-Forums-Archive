---
title: "Firefox is recognised wrong by the servers."
date: 2011-03-09
forum: Desktop Environments
---

### Post by vedovatti on 2011-03-09
Hi there,

my problem happened sinces a long time ago. Basically Firefox, when I try to download plugin from Google or from mozilla website or when I check my IP, the servers think that my Firefox is a 3.0.0 and **Window XP**.

I use Ubuntu 10.04 and the Firefox version 3.16.15 - Mozilla Firefox for Ubuntu canonical - 1.0. I attached to this a pic of what I get from the website: [www.whatismyip.com](www.whatismyip.com). It tells me that I am using XP, what a shame!.

Thanks

---

### Post by Krytarik on 2011-03-09
Please enter "about:config" into the location bar, then check if there is a key for "general.useragent.override". If so, right-click at it and choose "Reset", you may note its value before. This may also be caused by an active extension you have installed.

---

### Post by vedovatti on 2011-03-10
Danke schön!! It work out!

Solved!!!

Cheers

---

### Post by Krytarik on 2011-03-10
Wow, I really didn't think that it will be *that* easy! Cool! :)

---

