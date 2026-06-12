---
title: "Help with partitioning"
date: 2009-05-03
forum: General Help
---

### Post by dfreehill on 2009-05-03
I was wondering what is the best size partitioning (swap, /, /home)

I have 2gb of ram, what should the swap partition be it's now 2.8gb?

/ is 18.6 this seems large?

/home is 18.8 this is the rest of the space.

TIA!

Dan

---

### Post by killabee44 on 2009-05-03
> **dfreehill said:**
> I was wondering what is the best size partitioning (swap, /, /home)

I have 2gb of ram, what should the swap partition be it's now 2.8gb?

/ is 18.6 this seems large?

/home is 18.8 this is the rest of the space.

TIA!

Dan

Read here for partitioning info..

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

I hope that helps.

---

### Post by happyhamster on 2009-05-03
The amount of swap seems fine: it will even allow the system to hibernate if you choose to (when going into hibernation, the system writes the contents of RAM to disk).

/ is pretty large. I would go for something like:

/---------8 GB;
/home-----the rest;

An even smaller / partition (down to 5~6GB) should work too, but you could run into trouble because some applications can fill up /tmp very quickly.

In fact, on a small drive, I probably wouldn't use a separate /home partition. Good luck.

---

### Post by dfreehill on 2009-05-03
Thanks all

---

