---
title: "Ubuntu Dapper 6.06 Boot Problem"
date: 2006-08-23
forum: Desktop Environments
---

### Post by bench on 2006-08-23
I have a frustrating startup issue - right at the beginning of the sequence, before the bootsplash I have an approximately 80-90 second delay.  The output from dmesg reveals it as being between these two lines:

[17179572.860000] checking if image is initramfs... it is
[17179664.876000] Freeing initrd memory: 6817k freed

If I'm reading it right, this time it is 92 seconds.

The kernel I'm using is vmlinuz-2.6.15-26-686 (the same happens on the standard installed -386 version).

The kernel image etc is on a seperate /boot partition with ext3 fs.

I've read somewhere this could be an issue on slow, embedded machines - but this is a P4 laptop with 768Mb of RAM.

Anyone any ideas?

Thanks.

---

