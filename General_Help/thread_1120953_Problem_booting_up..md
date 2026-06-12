---
title: "Problem booting up."
date: 2009-04-09
forum: General Help
---

### Post by simen........... on 2009-04-09
Hi!

when I tried to start ubuntu i got this messages:
[o.oooooo] intrd extends beyond and end of memory (0x1be7fd58 > 0x1be00000)
[o.oooooo] disabling initrd
[0.032002] ..MP-BIOS bug: 8254 timer not connected to I0-APIC
[o.262147] Kernel panic - not syncing: VFS: Unable to mount root fs unknown-block(8,1)



what is the problem? ( i used Wubi to install)

---

### Post by simen........... on 2009-04-09
anyone?

---

### Post by simen........... on 2009-04-10
Anyone?

---

### Post by Alias1407 on 2009-04-10
I'll assume that you still have windows if you installed via wubi,
Boot up windows and go...

Start --> Run --> (type) cmd

A black window should open,

type...

```
chkdsk /r
```

this will scan and repair any errors in your disk. This will take some time depending on how big your drive is.

Then try booting up Ubuntu again.

If that doesnt work,

When grub is loading select the Ubuntu recovery mode and then select scan disks.

---

### Post by Thura on 2009-04-10
[http://www.ibm.com/developerworks/linux/library/l-boot-rootfs/index.html?S_TACT=105AGX03&S_CMP=EDU](http://www.ibm.com/developerworks/linux/library/l-boot-rootfs/index.html?S_TACT=105AGX03&S_CMP=EDU)

---

### Post by eirinikp on 2009-04-10
> **Thura said:**
> [http://www.ibm.com/developerworks/linux/library/l-boot-rootfs/index.html?S_TACT=105AGX03&S_CMP=EDU](http://www.ibm.com/developerworks/linux/library/l-boot-rootfs/index.html?S_TACT=105AGX03&S_CMP=EDU)

I have the same problem with simen. The page you sent proposes 4 tips. Which one should we follow?
I'm afraid that my problem is the key, because when I do sudo apt-get update it shows me at the end the following message:
W: GPG error: [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2EBC26B60C5A2783
W: You may want to run apt-get update to correct these problems

Any idea?
Thanks in advance!

---

