---
title: "Create NTFS partition with Fawn?"
date: 2007-05-17
forum: Desktop Environments
---

### Post by marty922 on 2007-05-17
G'day everyone,

With the introduction of NTFS read/write supported by Fawn, is it possible to create an NTFS partition within Ubuntu?

I've had a look at gparted and it has ntfs greyed out.

Is there another tool I could use?

Cheers,

Marty

---

### Post by taurus on 2007-05-17
Are you talking about resizing your / partition, creating another partition with ntfs filesystem?  If that the case, you cannot resize your / partition while you are using it.  You need to use the LiveCD or better yet, use the GParted LiveCD since it comes with the latest version of gparted.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by marty922 on 2007-05-18
> **taurus said:**
> Are you talking about resizing your / partition, creating another partition with ntfs filesystem?  If that the case, you cannot resize your / partition while you are using it.  You need to use the LiveCD or better yet, use the GParted LiveCD since it comes with the latest version of gparted.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

No, I'm talking about creating a new partition with NTFS.

Ie. I have a new external HDD that I would like to create with NTFS, but currently I only have access to Ubuntu to create and/or format partitions.

Cheers,

Marty.

---

### Post by taurus on 2007-05-18
Gparted would allow you to format a harddrive to ntfs too.

---

### Post by marty922 on 2007-05-19
> **marty922 said:**
> G'day everyone,

With the introduction of NTFS read/write supported by Fawn, is it possible to create an NTFS partition within Ubuntu?

**I've had a look at gparted and it has ntfs greyed out.**

Is there another tool I could use?

Cheers,

Marty

Just in case anyone is looking for help.

The version of gparted that I had installed didn't support NTFS out of the box.

I was directed to this site: [http://www.linux-ntfs.org/]("http://www.linux-ntfs.org/")

I needed to install ntfsprogs.

```
sudo apt-get install ntfsprogs
```

Voila!  I can now create NTFS paritions.

Cheers,

Marty

---

### Post by claypole on 2007-06-12
Thanks Marty, I had this exact problem.  Solved!! :D

---

