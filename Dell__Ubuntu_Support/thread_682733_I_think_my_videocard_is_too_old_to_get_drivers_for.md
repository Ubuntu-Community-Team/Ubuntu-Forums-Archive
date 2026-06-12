---
title: "I think my videocard is too old to get drivers for."
date: 2008-01-30
forum: Dell  Ubuntu Support
---

### Post by overlord_david on 2008-01-30
I've been using ubuntu ever since my windows XP died on me. My brother knows how to work it, I do not.

I can't seem to get/install correctly the drivers my videocard needs... It's a GeForce2. My brother called it Legacy... Saying that it's so old I wont be able to get any support for it. Neither of us know what to do about it other than shelling out too much money for a new videocard. 

Any ideas?

---

### Post by jclmusic on 2008-01-30
try this command:

sudo apt-get install nvidia-glx-legacy

or just use the generic drivers, such as vesa or nv.

---

### Post by notwen on 2008-01-30
What driver is Ubuntu currently using by default?  Does it not support the reso you're after?

---

### Post by MJN on 2008-01-30
What exact card is it? Post the output of **lspci |grep -i nvidia**

Mathew

---

