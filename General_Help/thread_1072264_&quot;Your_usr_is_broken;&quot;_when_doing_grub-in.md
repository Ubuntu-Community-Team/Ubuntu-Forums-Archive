---
title: "&quot;Your /usr is broken;&quot; when doing grub-install"
date: 2009-02-17
forum: General Help
---

### Post by arunkr on 2009-02-17
hi,
I am an Ubuntu 7.10 user. I loaded it with almost all applications I needed. That's why I am not going to install any new release because I need to install all those application again (Since I have to pay if my net usage is high, I can't download them again.)

To day, My partition structure is 
/dev/sda1 : Kubuntu root partition
/dev/sda2 : Ubuntu root partition
/dev/sda3 : windows
/dev/sda4 : extened partition
/dev/sda5 : /usr for kubuntu
/dev/sda6 : /usr for ubuntu
/dev/sda7 : /home for ubuntu 
......

Today I deleted /dev/sda1 and resized /dev/sda2 to include the space I got when I delete /dev/sda1 using gparted and using live cd.
now I have 3 primary partitions
1) /dev/sda2
2) /dev/sda3
3) Extened partition
When I restarted I got a black screen with* GRUB _ * and nothing will happen for hours.
Now I need to install grub on MBR, right?
So I inserted live cd and did
1)
$sudo grub
>find /boot/grub/stage1
   (hd0,1)
>setup (hd0,1)
I got an error message and if I am correct it says "Invalied device string"

2) 
sudo mount /dev/sda2 /mnt 
sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /proc /mnt/proc
chroot /mnt /bin/bash
grub-install /dev/sda2

I got an error message Your /usr is broken;please fix it before calling this wrapper

Is there any solution to get back into my ubuntu installation?
Please I need urgent reply.:(

---

### Post by plucky on 2009-02-17
> >setup (hd0,1)


This command is incorrect,it should be ```
root (hd0,1)
``` and then ```
setup (hd0)
```


See this [link](http://ubuntuforums.org/showthread.php?t=224351&highlight=grub+install)


Good Luck

---

### Post by heindsight on 2009-02-17
> **arunkr said:**
> 
2) 
sudo mount /dev/sda2 /mnt 
sudo mount -o bind /dev /mnt/dev
sudo mount -o bind /proc /mnt/proc
chroot /mnt /bin/bash
grub-install /dev/sda2

I got an error message Your /usr is broken;please fix it before calling this wrapper

Is there any solution to get back into my ubuntu installation?
Please I need urgent reply.:(

The reason you got the error about /usr is because you didn't create a /usr inside your chroot environment. From the partition info you posted, I gather that your /usr is on a separate partition, so you should have mounted that at /mnt/usr before running chroot.

---

### Post by arunkr on 2009-02-17
big disaster. :'-) ,
when I mounted /dev/sda2 on my puppy linux after issusing all those commands in my previous post using my kubuntu live cd, Alas I found my root partition get empty.
Still I have my /usr partion.
Is there any way to come out of this? ( Am I making my self fool???)
ie., Install ubuntu again in /dev/sda2 as only linux installation path.
Then edit /etc/fstab and correct /usr to /dev/sda7. 
Is that possible??

---

### Post by arunkr on 2009-02-17
I mean commands in my own first post.
I didn't unmount those partitions before reboot. Is that the cause for this?
If anyone knows how this happend, I can avoid it appening again.

---

