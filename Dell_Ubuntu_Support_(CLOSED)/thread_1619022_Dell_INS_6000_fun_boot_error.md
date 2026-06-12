---
title: "Dell INS 6000 fun boot error"
date: 2010-11-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by skooternb on 2010-11-11
[IMG]http://farm5.static.flickr.com/4010/5167056346_03ac341f6e_z.jpg[/IMG]Hello all!

Long time listener, first time caller.

This morning my lovely Dell decided after several weeks of running 10,10 steady gave me this long boot error in command.

Please advise!  I am also thinking of formating if that is the only option.

Thanks!

---

### Post by skooternb on 2010-11-11
I would assume that this is just an increasingly long boot process with initramfs?

Any help here would be great.

---

### Post by skooternb on 2010-11-11
Fixed.

---

### Post by skooternb on 2010-11-15
tHello all!

This lockup is back... any help?

---

### Post by skooternb on 2010-11-15
In case anyone is having the same issues, as I've seen in searching this and other forums...

The boot procedure is somehow not finding a harddrive or some type of bootable disk, so this thread was able to help me out:

[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/67256](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/67256)

The partition is somehow 'damaged' or unusable...

If you know the partition number you can type, in the grub editor (goto grub, then press 'e') root=/dev/sda1 where sda1 is the location of the partition running ubuntu.

Werd.  I hope I can help someone since noone bothered to reply to me.

Best...

---

