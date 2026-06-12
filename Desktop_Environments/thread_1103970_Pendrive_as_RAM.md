---
title: "Pendrive as RAM???"
date: 2009-03-23
forum: Desktop Environments
---

### Post by ambdeep on 2009-03-23
Is there any way by which we can use a pendrive as RAM on ubuntu....like in Vista



Just curious  ;)

---

### Post by mcduck on 2009-03-23
No, not as RAM. Even Vista doesn't do that, it would be pointless as those drives are ridiculously slow when compared to RAM.

What Vista does is that it uses the drive as a kind of swap, in this purpose a flash drive has better random access times than a normal hard disk has (although the drive won't last very long).

You could do the same in Ubuntu, but most likely your system isn't using much swap at all so you wouldn't get any actual benefits.

edit: A typical pen drive has read speed of about 20MB/s. Expensive SDD drives can go above 200MB/s. Typical RAM stick, DDR2-667 SDRAM, has transfer rate of 5333MB/s. ;)

---

### Post by ambdeep on 2009-03-23
Thanks!!

---

### Post by Marlonsm on 2009-03-23
just to complete mcduck's post:
an usual hard disk can transfer files at around 70Mb/s, but it takes longer to actually starting the transfer, so if you really need a bigger swap, a pen drive would be better than an HD for it.

---

### Post by albandy on 2009-03-23
> **Marlonsm said:**
> just to complete mcduck's post:
an usual hard disk can transfer files at around 70Mb/s, but it takes longer to actually starting the transfer, so if you really need a bigger swap, a pen drive would be better than an HD for it.

You can improve the acces time  by using a raid system, for example, if you've two hard disk, instead of using one partition of one of the 2 disk for swap, you can do a little raid partition in each disk and make a raid 0, then create a new swap filesystem in raid device.

---

### Post by mcduck on 2009-03-23
> **albandy said:**
> You can improve the acces time  by using a raid system, for example, if you've two hard disk, instead of using one partition of one of the 2 disk for swap, you can do a little raid partition in each disk and make a raid 0, then create a new swap filesystem in raid device.

..although you would in most cases get a lot better results by investing that money to buy more RAM. ;)

---

### Post by albandy on 2009-03-23
> **mcduck said:**
> ..although you would in most cases get a lot better results by investing that money to buy more RAM. ;)

yes your option is the best but we don't know if he could put/buy more RAM

---

