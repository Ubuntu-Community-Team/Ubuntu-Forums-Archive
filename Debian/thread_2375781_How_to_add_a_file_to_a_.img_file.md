---
title: "How to add a file to a .img file"
date: 2017-10-27
forum: Debian
---

### Post by kazakore on 2017-10-27
I've been trying to install a very old version of Debian for a broadcast server (no option to go with something newer) and having a lot of problems as the main image seems to be coded to only install from /cdrom even if booted from USB originally.

Eventually I found if I download hd-media/boot.img.gz uncompress it and dd the resultant .ing file to a usb key it boots and gets to a point where it says it's searching for the iso file, rather than specifically looking for the cdrom. Sounds promising....

So what I wanted to do was add the debian.iso file to the boot.img image.

What I tried (paths approx/removed)

# mkdir /mnt/boot
# mount -o loop if=boot.img of=/mnt/boot
# cp debian.iso /mnt/boot
# dd if=/dev/loop0 of=boot2.img

md5sum of boot.img and boot2.img were the same as I assume the loop device automatically writes to the file. I wasn't sure so created the second one to check.

After doing this it boots, I get the Spash screen but then it crashes and restarts the system.

I have managed to get to the install stage by using two separate USB keys but I would still like to know the correct way to do the above for future reference.

---

### Post by kazakore on 2017-10-28
Nobody?? Surely adding files to a bootable disk image isn't that rare a thing to want to do and somebody much know how....

---

### Post by kazakore on 2017-11-01
One final bump in the hope of an answer......

---

### Post by howefield on 2017-11-01
Thread moved to the "*Debian*" forum.

---

### Post by kazakore on 2017-11-06
> **howefield said:**
> Thread moved to the "*Debian*" forum.

Why when I was running Unbuntu on the computer I was trying to edit the image from. Just because the .img file in question was for Etch (debian 4.0) should make no different to the fact it's a Ubuntu (well general Linux) question....

But seems nobody was able to answer anyway..... :(

---

