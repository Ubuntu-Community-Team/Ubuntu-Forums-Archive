---
title: "Simple question"
date: 2005-06-14
forum: Desktop Environments
---

### Post by Fozer on 2005-06-14
During the original setup of Ubuntu, I forgot to choose the resolution I wanted, and am stuck with, well, one I didn't want. So basically what I'm wondering is how to get back into that setup or some sort of facsimile of it. I'm sure it's right in front of my eyes, but help is still appreciated.

---

### Post by Leif on 2005-06-14
open a terminal and type "sudo dkpg-reconfigure xserver-xorg"

---

### Post by Curlydave on 2005-06-14
Upon doing so, the answer is "space", not "enter".

---

### Post by az on 2005-06-14
You can also just pick the xserver-xorg package in synaptic and use the configure option in the drop-down menu.

If you have a really old card, you can lower the color depth to 16-bit to get higher screen resolutions.

The advatage to reconfiguring xserver-xorg from the comman line is that if your xserver does not start, you can just reconfigure it again.  Also, you cannot autodetect hardware when you are running x.

---

