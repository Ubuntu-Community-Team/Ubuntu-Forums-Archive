---
title: "dmcrypt, several partitions, one password"
date: 2009-02-04
forum: General Help
---

### Post by cleric23 on 2009-02-04
Hey everybody,

I am playing around with dmcrypt. What I have right now is a /boot partition (unencrypted) with an initrd, a root partition, a home partition and a swap partition, all of them encrypted by the **same** password. swap is also encrypted using the password (and not random data) because I use swap for suspend to disk (which already works fine, while using dmcrypt).

My problem is: When I boot the system, I have to type in the same password multiple times. That really bugs me. What I basically want is, that the system tries to use the password, which was correct for the first disc, to unlock the second disc, and so on.

I found some patches:
* [https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/139057](https://bugs.launchpad.net/ubuntu/+source/cryptsetup/+bug/139057)
* [http://wiki.yobi.be/wiki/LUKS#Avoiding_to_type_many_times_the_LUKS_password](http://wiki.yobi.be/wiki/LUKS#Avoiding_to_type_many_times_the_LUKS_password)

But they all do not apply clean and dont work like they should.

Is there really no easy way to do this?!

(For several reasons, I dont want to use LVM nor do I want to use key files for all but the root partition. I really WANT passwords).

Thanks in advance!

Flo

---

### Post by cleric23 on 2009-02-06
nobody? :-(

---

### Post by hyper_ch on 2009-02-06
I've written a howto for using a keyfile to unlock partitions. You can find it here in the tutorials section.

---

### Post by cleric23 on 2009-02-06
Yeah, thank you, I already know that howto. But as I said, I dont want to use keyfiles, at least not stored on my disk. And I dont want to use an USB stick either. I really want passphrases :-) Just dont want to type them in multiple times :-(

---

### Post by hyper_ch on 2009-02-06
then you're out of luck

---

