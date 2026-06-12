---
title: "Changing the size of a .img file"
date: 2008-11-12
forum: Desktop Environments
---

### Post by Timana on 2008-11-12
Hi, I burnt a ubuntu minimal image off a 256MB flash card, and want to copy it onto a 1GB card. Is there a way I can do this using the 'dd' command so that ubuntu will run on the whole card and not just the first 256MB.

Cheers,

T.

---

### Post by larseko on 2008-11-12
Not sure if it will work, but if you first dd the image to the 1GB card, you could probably open the memory card in gparted or similar afterwards and resize the partition from 256MB to 1GB?

---

### Post by Timana on 2008-11-13
Thanks for your help larseko.

I copied the image first and then used gparted and it work fine.

Thanks again.

---

