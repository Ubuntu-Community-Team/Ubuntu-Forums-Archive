---
title: "new dell netbook"
date: 2009-12-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by trixman on 2009-12-03
a quick question my brother is about to purchase soon his first linux ubuntu through dell and is looking at the new netbook. does anydody have any info on how nice these systems are.

---

### Post by mikewhatever on 2009-12-03
What do you mean by 'how nice'? What do you want to know?
I have a mini 10, with infamous gma500. It was kind of tricky to set up, but I quite like the way it is now. I don't think Ubuntu is offered with gma500 though, and other models should just work out of the box. So, in short, no complains.

---

### Post by trixman on 2009-12-03
> **mikewhatever said:**
> What do you mean by 'how nice'? What do you want to know?
I have a mini 10, with infamous gma500. It was kind of tricky to set up, but I quite like the way it is now. I don't think Ubuntu is offered with gma500 though, and other models should just work out of the box. So, in short, no complains.

i was just wondering how it worked right out of the box, but thanks for the reply

---

### Post by TCSnyder on 2009-12-03
i got the dell mini 10 with ubuntu out of the box.

it worked ok, but i like the original ubuntu better do i formatted it. i would recomment getting xp (or 7) on it and dual boot

and yes dell had a gma500 driver for it, but it was made for some crazy architecture lpia i think, so there is my 2 cents

---

### Post by mikewhatever on 2009-12-04
> **TCSnyder said:**
> i got the dell mini 10 with ubuntu out of the box.

it worked ok, but i like the original ubuntu better do i formatted it. i would recomment getting xp (or 7) on it and dual boot

This doesn't make sense, I mean, you like Ubuntu, but recommend paying Windows tax.:confused:

> and yes dell had a gma500 driver for it, but it was made for some crazy architecture lpia i think, so there is my 2 cents

Well, lpia is an architecture developed by Intel, with some optimizations for Atom CPUs. I think it could have been much crazier then that. Anyway, you can always install a regular i386. I've tested Fedora12 and Mandriva on mine, both worked ok, and Mandriva even supported gma500 out of the box.

---

### Post by Jackyboy86 on 2009-12-04
There is now a driver for the GMA500 made by lukazade which clears up the whole driver thang with the mini 10 - it uses backports.
BUT, you have to reinstall them everytime you upgrade the kernel.
I'd be weighted towards a 10v - it's got a different videocard...

---

### Post by LiamWilson on 2009-12-04
Yeah, I got the Dell Mini 10v, and it works perfectly with the Dell version of Ubuntu you get with it, and perfectly too with the latest version of Ubuntu Netbook Remix you can download. I love it! :D

---

### Post by trixman on 2009-12-04
> **LiamWilson said:**
> Yeah, I got the Dell Mini 10v, and it works perfectly with the Dell version of Ubuntu you get with it, and perfectly too with the latest version of Ubuntu Netbook Remix you can download. I love it! :D

thanks for the replys, my brother ordered the new dell netbook 10 
he upgraded the memory to 2 gig & the hard drive to 250. 
he saw my hardy heron and just liked it and purchased a linux laptop instead of windows 7, not anti windows just liked the feel of ubuntu.


thanks to all for the nice help

---

### Post by mikewhatever on 2009-12-04
> **Jackyboy86 said:**
> There is now a driver for the GMA500 made by lukazade which clears up the whole driver thang with the mini 10 - it uses backports.
BUT, you have to reinstall them everytime you upgrade the kernel.
I'd be weighted towards a 10v - it's got a different videocard...

Actually, you can use dkms to autoinstal it. Run 'locate dkms.conf', to locate the relevant psb related dkms.conf files. In my case, they are:

```
/usr/src/psb-kernel-source-4.41.1/dkms.conf
/var/lib/dkms/psb-kernel-source/4.41.1/build/dkms.conf
```

Now, add <AUTOINSTALL="yes"> without the brackets to both. That should take care of the psb driver on kernel upgrades.

---

