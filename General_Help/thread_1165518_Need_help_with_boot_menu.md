---
title: "Need help with boot menu"
date: 2009-05-20
forum: General Help
---

### Post by newntlam on 2009-05-20
I need help with menu.lst
I accidentally set timeout = 0, and the default boot is windows. Now every time it boots into windows without giving me a chance to choose. How can I get back to ubuntu to edit the menu.lst?

Thanks,

Lam

---

### Post by adam@home on 2009-05-20
Use the Install CD, boot to a Live Session edit as root menu.lst on the disk, save and restart (remove the CD!)

---

### Post by newntlam on 2009-05-20
I can not cd to boot/grubs.

Where is the menu.lst located now? Do I have to do some mounting?

Thanks,

---

### Post by whitethorn on 2009-05-20
I think the commands should be something like this

First you gotta find out which HD, partition your / is on.  I think 

```

sudo fdisk -l 

```
Should display your the partition table.  You could also start Partition Editor (Administration -> Partition Editor).  Once you've found which partition your / is on. We can mount it. It should be something like sda3 (first HD 3 partition).

```

sudo mkdir /media/ubuntu
sudo mount /dev/sda3 /media/ubuntu
ls /media/ubuntu/

```


If you choose the right partition you should be able to see your / .  If you don't know which partition to mount, post the output from.

```

sudo fdisk -l

```

---

### Post by adam@home on 2009-05-20
Try browsing for your hard disk with the ubuntu installation via nautilus/file browser. Using 'cd' in terminal will result in browsing the live session.

---

### Post by newntlam on 2009-05-20
Here is what i did:

sudo mkdir /mnt/root

sudo mount -t ext3 /dev/sda3 /mnt/root

cd /mnt/root/boot/grub

sudo vim menu.lst

and then change timeout 0 --->1

reboot

Thanks for all your help. 

Now I have another problem (actually I had this problem before changing timeout).
The selection which is supposed to boot automatically in 1 second won't boot. I have to touch the Enter key in order to get it booted.
How do I fix this?

Thanks

---

