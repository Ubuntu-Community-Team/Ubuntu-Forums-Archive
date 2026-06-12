---
title: "Glest"
date: 2006-08-08
forum: Gaming &amp; Leisure
---

### Post by ojinka on 2006-08-08
Hi, i downloaded Glest, instaled it, but there is some problem with my sound card.


gpeter@prescott:~$ glest
bash: glest: príkaz nenájdený
peter@prescott:~$ /home/peter/glest/glest
OpenAL Vendor: J. Valenzuela
OpenAL Version: 0.0.8
OpenAL Renderer: Software
OpenAl Extensions: Software
Exception: Couldn't select audio context: ALC_INVALID_DEVICE

What can i do?
Thanks ;)

---

### Post by ojinka on 2006-08-08
no ideas? :sad:

---

### Post by Frem on 2006-08-09
The problem is obvious: Your sound card uses the xara20m driver, which is incompatible with Glest. You need to install the latest Ubuntu kernel update and edit your /lib/kernel/2...

No, seriously. The model of your sound card and what sound system you are using would also help. Have you installed the OpenAL lib stuff?

---

### Post by ojinka on 2006-08-09
I have realtek AC 97 on my motherboard, and how can i found out if i installed the OpenAL lib stuff?

---

### Post by ojinka on 2006-08-09
Ok, i found a solution.
Just download and install libopenal-dev :)

---

### Post by SanskritFritz on 2008-01-20
Thank you, that was a good solution for me as well!

---

