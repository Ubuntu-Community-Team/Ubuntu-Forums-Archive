---
title: "Automount problem with udf CDs"
date: 2005-12-05
forum: Desktop Environments
---

### Post by gi2k15 on 2005-12-05
Hello, people.

I'm having problems with automount when it comes to UDF CDs. It simply does nothing, as if there wasn't a CD in the drive. Automount works well with ISO CDs though.

I am able to mount manually using:

```
sudo mount -t udf /dev/cdrom /media/cdrom0
```

umount sometimes fails saying the device is being used, but sometimes too it works.

Any suggestions on how making automount works for UDF CDs?

Thanks.

---

### Post by dcstar on 2005-12-06
[QUOTE=gi2k15]Hello, people.

I'm having problems with automount when it comes to UDF CDs. It simply does nothing, as if there wasn't a CD in the drive. Automount works well with ISO CDs though.

I am able to mount manually using:

```
sudo mount -t udf /dev/cdrom /media/cdrom0
```

umount sometimes fails saying the device is being used, but sometimes too it works.

Any suggestions on how making automount works for UDF CDs?

Thanks.[/QUOTE]
Firstly, I installed the pmount package (and removed the nautilus stuff, just too unreliable), then this link is useful:

[http://www.raoul.shacknet.nu/2005/11/10/packet-writing-on-cdrw-and-dvdrw-media/](http://www.raoul.shacknet.nu/2005/11/10/packet-writing-on-cdrw-and-dvdrw-media/)

The script needs a little modification to work with Ubuntu, but it helped me get my UDF stuff going!

---

