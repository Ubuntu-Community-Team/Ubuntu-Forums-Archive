---
title: "Can't detect external USB HD"
date: 2007-07-06
forum: Dell  Ubuntu Support
---

### Post by feedmecereal on 2007-07-06
I have two external hard drives and I can't get Ubuntu to detect either one. Under Ubuntu, I turn on either drive and nothing seems to happen. One I just put together myself and the other I bought prebuilt. I could get the drive detected under Windows XP with the one that is prebuilt if I turned it on and unplugged and replugged the USB connection.

I am having this problem on two different computers. One is a Dell I just bought with Ubuntu preinstalled.

How can I get the new drive to work under Ubuntu?

---

### Post by Rocket2DMn on 2007-07-06
Plug the harddrives in and power them up.  After this is done, open up a terminal and type "fdisk -l" and copy and paste the output to this thread.  It is likely that the drives just need to be mounted.
If the drives are formatted with NTFS (quite likely if you set them up initially with windows), you will need to download ntfs-3g which allows you to read/write NTFS drives.

---

### Post by feedmecereal on 2007-07-06
I got the following output:

```
Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641    7  HPFS/NTFS

```

Also, I forgot to mention that this HD was encrypted using Truecrypt.

---

### Post by neptho on 2007-07-06
[QUOTE=feedmecereal]Also, I forgot to mention that this HD was encrypted using Truecrypt.[/QUOTE]

That'll do it if the whole thing is TrueCrypt; it sees that it's NTFS, but TrueCrypt is not installed, so it just says 'huh?'  [Try following this HOWTO](http://techystuff.info/?p=28), it's a little short for those new to Ubuntu and Linux, but it gets most of the points across.  :)

---

