---
title: "Windows Re-install vs GRUB, Round 2"
date: 2006-10-03
forum: Desktop Environments
---

### Post by RAdams on 2006-10-03
I reinstalled Windows recently, knowing full well it would overwrite my MBR. Restoring GRUB went fine, except now I can't boot Windows. The old settings won't work, because Windows got all in a tizzy about my shared FAT32 partition, making that "Drive C", and its partition "Drive D".

So here's the question: when you first install Ubuntu, it automagically detects "other operating systems" and loads them into menu.lst. How can I force that to happen again?

---

### Post by hulet on 2006-10-03
> **RAdams said:**
> I reinstalled Windows recently, knowing full well it would overwrite my MBR. Restoring GRUB went fine, except now I can't boot Windows. The old settings won't work, because Windows got all in a tizzy about my shared FAT32 partition, making that "Drive C", and its partition "Drive D".

So here's the question: when you first install Ubuntu, it automagically detects "other operating systems" and loads them into menu.lst. How can I force that to happen again?

Don't really know how exactly to do what you asked but you can yourself easily edit your menu.lst if you know the drive configurations. Can you post your working /etc/fstab and /boot/grub/menu.lst file.

---

### Post by RAdams on 2006-10-03
What I was asking is: when you first install Ubuntu, it detects Windows and other operating systems automatically and writes in the boot instructions into menu.lst.

I know about editing menu.lst.

I'll post my fstab and menu.lst when I can. Thanks.

---

### Post by RAdams on 2006-10-04
my menu.lst: [http://pastebin.com/799993](http://pastebin.com/799993)
my fstab: [http://pastebin.com/799997](http://pastebin.com/799997)

---

### Post by RAdams on 2006-10-04
Not to be one of those annoying thread-bumpers... but I'm genuinely stumped here, and I'd like to be able to properly boot up again... any ideas?

---

### Post by RAdams on 2006-10-09
...

I REALLY need some help... I'm stumped... anyone?!

---

