---
title: "How to add a second hard disk without re-format?"
date: 2009-01-03
forum: General Help
---

### Post by dub_u on 2009-01-03
I want to add a second HD to my Xubuntu machine, but I can't figure out really how to.

Background (short version)

My friend has a computer (slow one) with Xubuntu installed on a 8GB HD.
I want to help my friend, so I prepare a faster computer that I don't need by installing Xubuntu Intrepid. Unfortunate I only have a 2.5GB HD. 
Anyway, I installed the system and removed some software I know she would not need (Gimp etc.), now there is only 50MB left of the 2.5GB disk.
On the original 8GB disk there is a lot of music and stuff so I don't want to format the drive.

I tried tonight to mount sdb1 as /home but that left me with a corrupt system that I hardly managed to recover ;-)

Both disks have 2 partitions, one / and one swap partition.
I want to get rid of the swap partition on sda and increase the size of sda1 to maximum (will give me a few hundred MB extra for VLC and other software I promised to install)
and then use sdb1 as home partition and use the swap on sdb2.

And this without formatting any of the disks. It is possible?

Hopfully someone understands my problem and can help me out.

---

### Post by Polygon on 2009-01-03
just plug in the second hard drive to your computer, and it should show up. then you can remove partitions, move files, etc on either hard disk with no problem

---

### Post by dub_u on 2009-01-03
With GParted you mean?
I tried that, but it wouldn't let me increase sda1...
And I don't know how to mount the second disk properly.
When I tried with
```
sudo mount /dev/sdb1 /home
```
I couldn't log in properly...

---

### Post by Polygon on 2009-01-03
do you want to switch hard drives? so the root partition is on the hard drive you are plugging in?

by default ubuntu should mount the second hard drive into like /media/whatever.... but if you want to move your home directory to your new hard drive, i think it would be easier just to reinstall ubuntu onto that new hard drive, or just create another user and set its home directory to /home on the second hard drive

---

### Post by dub_u on 2009-01-03
The thing is that it is not mounted as /media/whatever. The only thing in /media/ is /cdrom

But the idea of adding a new user with home on the new hard drive is interesting...I don't want to re-install, since there is so much music on the new hard drive (and on one partition only)

I don't have the computer with me any longer so I can't try, but that would probably solve it.

And I read somewhere that the swap can be "anywhere" (?) so if I can resize the old root to 100% of the disk and place swap on the new disk plus add a new user with home partition on the new disk I am probably where I want to be...

---

### Post by dub_u on 2009-01-20
It's solved. The disk wasn't properly connected :oops: that's why it wasn't recognized bu Xubuntu...
So now I'm running Xubuntu 8.10 on the new (2.5GB) disk with /home on the old disk (8GB)
(created a new user as Polygon suggested)

---

