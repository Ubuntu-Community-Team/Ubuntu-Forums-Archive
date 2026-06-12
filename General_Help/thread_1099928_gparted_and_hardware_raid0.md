---
title: "gparted and hardware raid0?"
date: 2009-03-18
forum: General Help
---

### Post by skelooth on 2009-03-18
Quick question,

Can I use the live CD to repartition my raid0? I'd like to install ubuntu on this pc. GParted shows my two 512 drives as one 1tb drive. Is it safe to resize it with gparted?

---

### Post by MaindotC on 2009-03-18
I googled "gparted raid" and there were mixed replies.  Some people said it worked great, some declared there was no driver for gparted itself but the livecd of an o/s, such as Ubuntu, contained RAID support.  Just go ahead and try it - what's the worst that could happen.

---

### Post by skelooth on 2009-03-18
We know what the worst can happen is. Those are the same types of results I found on google too. Hopefully someone has some experience with this type of set up.

---

### Post by skelooth on 2009-03-18
found it.
> 
GParted supports fully hardware RAID controllers (level 5 as well as other RAID levels). It doesn't support software RAID solutions. 
From a moderator at [http://gparted-forum.surf4.info/viewtopic.php?id=510](http://gparted-forum.surf4.info/viewtopic.php?id=510)

So the worst that happens is it complains it's missing something. Thanks.

---

### Post by MaindotC on 2009-03-18
Figured it wouldn't be a horrible issue.  Hope it works out well for you.

---

