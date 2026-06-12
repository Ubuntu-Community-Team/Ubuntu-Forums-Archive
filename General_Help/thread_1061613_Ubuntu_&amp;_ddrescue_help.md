---
title: "Ubuntu &amp; ddrescue help"
date: 2009-02-06
forum: General Help
---

### Post by bennco9 on 2009-02-06
I need some help. I am a Windows person and have NO unix experience at all. I have a hard drive that has several bad sectors and am trying to recover the data.

I have read several forums that say that ddrescue is the way to go. So I have downloaded Ubuntu desktop 8.10 and burned it to a CD.

I booted into Ubuntu, but the interface looks so incredibly foreign to me and have not idea really how to navigate. I also have no idea how to download, or install, or use ddrescue.

Can someone help? I would really appreciate any and all help! Just for the record, I have been wanting learn start playing around with Ubuntu, just wasn't sure where or how to start.

Thank you very, very much.
Jonathan

---

### Post by jerome1232 on 2009-02-06
I'm by no means an expert using ddrescue but I can help with basic usage.

First you need to install it, from a terminal, Applications-Accessories-Terminal;

```
sudo apt-get install ddrescue
```

determine what partition it is you wish to rescue by listing out your partitions, also you need to know what disc your going to copy the image to.

```
sudo fdisk -l
```

let's say you want to rescue /dev/sdb2 and copy the image to /dev/sda1.

```
sudo mount /dev/sda1 /mnt
sudo ddrescue /dev/sdb2 /mnt/mydisk.img
```

You can then fsck that image file and then mount it

```
fsck -f /mnt/mydisk.img
mkdir /mnt/mydisk 
mount /mnt/mydisk /mnt/mydisk.img -o loop
```

then have a look and see if it's working. Definitely feel free to ask questions before you leap as I'm positive my explanation leaves much to be desired.

---

### Post by bennco9 on 2009-02-06
First of all, Jerome1232, thank you very much for your reply! 
So I would need to have 3 hard drives in this system? One to mount Ubuntu itself, the bad drive, then a good drive to recover to? Can I mount the fs to a thumb drive?

Thanks,
Jonathan

---

### Post by jerome1232 on 2009-02-06
Since you can run Ubuntu from the live cd you only need 2 drives, the bad one and then a good one to recover to. The good one will need to be at least as big as the bad one.

---

### Post by bennco9 on 2009-02-26
Thanks so much for your help Jerome1232! Your instructions were right on the money. The only difference was I had to figure out how to partition the new drive in Ubuntu, but a simple google search helped me with that.

You saved me A LOT of headache. Thank you very much. And I might add that ddrescue worked flawlessly on a drive that had 3 bad sectors and failed every other windows imaging app that I could find.

---

### Post by jerome1232 on 2009-02-27
> **bennco9 said:**
> Thanks so much for your help Jerome1232! Your instructions were right on the money. The only difference was I had to figure out how to partition the new drive in Ubuntu, but a simple google search helped me with that.

You saved me A LOT of headache. Thank you very much. And I might add that ddrescue worked flawlessly on a drive that had 3 bad sectors and failed every other windows imaging app that I could find.

Glad I was able to help you out :) Hopefully no important files were lost.

---

