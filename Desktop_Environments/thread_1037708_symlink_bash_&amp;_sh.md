---
title: "symlink bash &amp; sh"
date: 2009-01-12
forum: Desktop Environments
---

### Post by iferq on 2009-01-12
Hey guys,

Did something really stupid, while trying to install the Lotus Notes client for Firefox in Ubuntu Hardy (which eventually hasn't worked so far).

This is what I did after which everything is messed up:
ln -sf /bin/bash /bin/sh

Now the system won't start as it can't find bash. I can't locate the exact startup script that invokes bash, thus can't change it back. Please tell me how I can fix this!!

Have even tried restoring using the CD, server setup won't go beyond a certain point (as it can't find bash). Only option left is to reinstall afresh.

Thanks,
Amit.

---

### Post by jpkotta on 2009-01-12
Boot from a Live CD, mount your hard drive, and link /bin/dash to /bin/sh.

But I'm confused.  The command you gave should not have touched bash, nor done anything bad.  In fact it should have changed /bin/sh to how it was pre-Dapper.

---

### Post by iferq on 2009-01-22
> **jpkotta said:**
> Boot from a Live CD, mount your hard drive, and link /bin/dash to /bin/sh.

But I'm confused.  The command you gave should not have touched bash, nor done anything bad.  In fact it should have changed /bin/sh to how it was pre-Dapper.


Hey thanks jpkotta!! Did a little bit of sniffing around the forums and solved the problem:

Booted from Live CD
Checked mount-able drives: sudo fdisk -l
Created a mount point: sudo mkdir /media/sda6
Mounted Ubuntu partition: sudo mount /dev/sda6 /media/sda6

Deleted old sh: sudo rm -f /media/sda6/bin/sh
Re-created symlink: sudo ln -sf /bin/bash /media/sda6/bin/sh

Voila!!

Thanks a ton for giving me the right first step :p
After my system rebooted normally, I was just wondering how come I din't think of something so easy!! LOL!!

Thanks anyway!

Problem Solved!

---

