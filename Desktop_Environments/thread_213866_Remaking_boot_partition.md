---
title: "Remaking boot partition"
date: 2006-07-11
forum: Desktop Environments
---

### Post by Cheator on 2006-07-11
Wow. Big mistake today. I formated my boot partition and now i can't boot. I was wondering how easy it would be to remake it? Boy i am dumb :)

---

### Post by glotz on 2006-07-11
I think you can fix it like this. Boot onto the CD and and copy the /boot to your mounted HD /boot.

---

### Post by Cheator on 2006-07-11
> **glotz said:**
> I think you can fix it like this. Boot onto the CD and and copy the /boot to your mounted HD /boot.

I just tried it with no success. I am getting an Error 17 with grub, and my boot partition is a partition on it's own (hdc1)

---

### Post by glotz on 2006-07-11
You might need to edit /boot/grub/menu.lst (on the HD!). Make sure the disk and partitions are corretly set. [GRUB stage2 errors](http://www.gnu.org/software/grub/manual/html_node/Stage2-errors.html#Stage2-errors )

---

### Post by Cheator on 2006-07-11
Thanks for the reply! I don't have a grub directory though since I deleted the partition. would grub-install do it or does that install just the MBR jazz?

---

### Post by glotz on 2006-07-11
You're welcome. I don't know. Somebody else surely will.

---

### Post by Cheator on 2006-07-11
Thanks! I got it to make the map file, but I can't seem to use the thing properly. I am told to do grub-install --root-directory=/boot hd2 (I think its hd2 in this case, it being hdc). Am i on the right track?

---

### Post by Cheator on 2006-07-11
I seem to have gotten farther. I am using --root-directory=/boot hd0 but it gives me an error of /boot/grub/stage1 not read correctly

---

### Post by glotz on 2006-07-11
EDIT: I'm fresh out of ideas, I hope somebody will be able to help you out. If you want, I can send you copy of my /boot... (I'm on the newest 686 kernel) You will still need to edit the menu.lst to represent your system layout naturally.

---

### Post by Cheator on 2006-07-12
@glotz: ?

Anyone?

---

