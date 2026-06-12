---
title: "ADDING WinXP install to current Ubuntu - any suggestions?"
date: 2008-12-14
forum: Desktop Environments
---

### Post by Martyn Thompson on 2008-12-14
Hi guy and gals.

I have a laptop that I use at home but belongs to my work.  This has Windows XP on and is supported by our IT department. I do NOT have admin access rights to XP. 

As I have a greater affinity to Ubuntu the first thing I did was remove the works hard drive (40GB) and add my own bought one (120GB). I installed Ubuntu on to my own drive and I am more than happy with this system. 

HOWEVER (this is the rub). I sometimes need to use the WinXP hard drive to connect into work to securely read emails keep in touch with the office. For the last 6 months I have been doing this by swapping the drives over but obviously that is a pain to do and I am sure long term it won't be doing either HDD a lot of good. 

So my question is (sorry for going round the houses but I thought it was important that you know the background), does anyone know of any software that will allow me to make a complete image of the WinXP installation and put it on to my own 120GB disk, then allow me to dual boot? 

Further, I already have a nice Ubuntu set up on my current disk and would prefer not to have to reinstall if possible, but recognise I may be forced to. 

I do not have Admin rights to the XP installation (as I said, it is maintained by IT). It also uses Cisco software to connect to my office which is why I need a complete image.  My intentions are not to try and break the existing Win XP install and I certainly have no intentions of trying to circumnavigate the security in place on this... my intention is just to make my life easier and save wear/tear on the hardware (and my time). 

I realise this is a big ask and wondered if anyone has any thoughts (apart from 'Don't do it!'). 

I have seen nLite - will this do the job for me? 

Thanks in advance,


Martyn.

---

### Post by sigurnjak on 2008-12-14
Well i se3 you are in a little bit of a pickle there !

These are just suggestions , so play carefully !

1 put your xp back in and use northon ghost or something similar to image your xp to a external drive 

2 put your ubuntu back  and try resizing your ubuntu partition to make room for your xp

3 put ghost cd back in with external hd /xp image pluged in and try cloning xp to a empty space 

4 rerun grub from live cd if necessary or add xp like i did here to your grub list 
[http://forumubuntusoftware.info/viewtopic.php?f=43&t=1939](http://forumubuntusoftware.info/viewtopic.php?f=43&t=1939)

Hopefully this gets you somewhere ! ):P

---

### Post by caljohnsmith on 2008-12-14
You could first use Ubuntu's partition editor gparted (System > Admin > Partition Editor) from the Live CD to resize your Ubuntu partitions on the Ubuntu drive to make room for the XP partition. Then you could use something like [Clonezilla]("http://www.clonezilla.org") or Partimage (it's in the repositories) to clone the XP partition to your Ubuntu drive. One of the keys to make it work though would be to make sure the XP partition you create on your Ubuntu drive starts at exactly the same sector as the XP partition on the Windows drive, otherwise you will run into complications. You can check where the partitions start by opening a terminal (Applications > Accessories > Terminal) and do:
```
sudo fdisk -lu
```
And that will show you the start/end points of the partitions in sectors. Anyway, that's the general idea of how I would do it, but if you want more specific directions, how about posting the output of the fdisk command while you have both drives connected. Or can you have both drives connected at the same time (is that part of the issue)?

---

### Post by Martyn Thompson on 2008-12-14
Thanks for the suggestions gentlemen. I will be careful (ha ha) but I am willing to have a go and try these ideas...

I will try this over the next few days so wish me luck!

Regards, 


Martyn.

---

### Post by sigurnjak on 2008-12-16
Good luck!):P

---

### Post by iggykoopa on 2008-12-16
if you have a way you can hook up both drives at once you could make a disk image of the xp install and run it in virtualbox.(if you can't hook up both drives at once but have another computer you could use a livecd like parted magic to make the disk image and transfer it over the network)

boot up into ubuntu then

1. find the xp disk name
```

sudo fdisk -l

```
you'll be looking for what drive it's on not the partition, it will probably be sdb. Then make a image of it on your ubuntu install
```

sudo dd if=/dev/sdb of=/home/yourusername/xp.dd

```
then convert the disk image to a virtualbox disk image
```

VBoxManage convertdd /home/yourusername/xp.dd /home/yourusername/xp.vdi

```
you should be able to load up that vdi image in virtualbox and you won't even have to dualboot.

---

### Post by sigurnjak on 2008-12-16
Thanks iggykoopa ! Just what i vas looking for !

---

### Post by iggykoopa on 2008-12-16
Hope it works for you.. I haven't personally tried it but the instructions I gave you are from guides I found on the net. Let me know how it works out.

---

### Post by samden on 2008-12-16
Just an idea, no idea whether it would work but if it did it may be simpler. Would you be able to buy a USB external hard drive case, put the work hard drive in that, then just plug that in and boot from it when you need to? If it worked it would save some fuss, but wouldn't be as convenient.

Just something that occurred to me, but someone here with more expertise can probably say why it wouldn't work!

---

### Post by iggykoopa on 2008-12-16
thats a great idea too samden, thats what I love about this stuff. So many ways to solve a problem.

---

