---
title: "dma cd drive"
date: 2005-06-06
forum: Desktop Environments
---

### Post by arendald on 2005-06-06
Hello

Apparently on kubuntu dma is not set on by default on cd/dvd drive/writer.
I know how to do that on console but I'd like to know what is the right place to do that in kubuntu for having dma on at each boot.
I'm looking for the right file/place to do that for kubuntu precisely not for any distro.

Thanks

---

### Post by Leif on 2005-06-06
You need to add something like the following to your /etc/hdparm.conf file

/dev/hdc {
dma = on
}

Of course, change hdc to suit your needs (pop in a cd, then type ls /dev/hdc to see whether it's the right location).

---

### Post by arendald on 2005-06-07
Thank you ;-)

A question, is there any particular reason dma is off on cd/dvd drives on kubuntu ?

---

### Post by Leif on 2005-06-07
Because there are still older drives that can have problems, or even get damaged, if dma is turned on by default. Hopefully this will get automated in the near future.

---

### Post by arendald on 2005-06-07
ok, does make sense.

---

