---
title: "Boot Problem : Urgent Help Needs !!!!!!!!! :("
date: 2010-02-19
forum: Desktop Environments
---

### Post by kiran88pnjr on 2010-02-19
Hai............

I need urgent help.............:(:(:(:(:(:(

I'm currently using Ubuntu 9.10. It was working perfectly till yesterday befo4 shutting down. 2day morning when I booted into Ubuntu it stops in the phase shown in the picture below. 

[IMG]http://cdn.cbsi.com.au/story_media/339299234/ubuntu-910-karmic-koala_1.jpg[/IMG]

It showed a message :

> 
" One or more of the mounts listed in /etc/fstab cannot yet be mounted :

  /home :waiting for UUID = 16db8ad1-281d-422b-959c-3e8382bf1fdc

  Press ESC to enter recovery shell "

I pressed 'ESC' and entered into recovery shell. I don't know what to do within that. Don't know any commands to recover my OS. 

I have shutdown my computer normally. I don't know what happened. If anyone knows please help me to recover my OS.

---

### Post by Pabloincarnate on 2010-02-19
I'm a noob to ubuntu and I had that problem once and all i did was boot from my ubuntu cd and that fixed it.

---

### Post by kiran88pnjr on 2010-02-19
> **Pabloincarnate said:**
> I'm a noob to ubuntu and I had that problem once and all i did was boot from my ubuntu cd and that fixed it.

How do u fixed that ?

---

### Post by amsterdamharu on 2010-02-19
Some problem with your harddisk or at least the home partition.

In the command shell can you check the following:

```
ls -l /dev/disk/byuuid/16db8ad1(press tab here to finish the command)
more /etc/fstab
```

If you cannot mount your home folder than you might not be able to log into gnome even if you fix the boot problem. 
To fix your boot problem you can not let it mount your homefolder and use testdisk to check and repair that partition.

To install testdisk:

```
sudo apt-get install testdisk
```

To not mount your homefolder (if testdisk cannot repair your home partition).

```
sudo nano /etc/fstab
```
this should open the fstab in an editor, you can put the # sign in front of the line that mounts your homefolder (tip it's the line that has /home in it).

---

### Post by nuwave on 2010-02-19
you seem to be having the same issue i had though there is a slight difference in your error message but here is how I got help to fix my problem

[http://ubuntuforums.org/showthread.php?t=1397193](http://ubuntuforums.org/showthread.php?t=1397193)

read the entire thread to make sure you have the same problem and the final solution is on the last page posted by meierfra

---

### Post by amsterdamharu on 2010-02-19
[update] First we need to know what's in the fstab to see what partition is giving you grief.

In short if the problem is the same than this should be the solution:

```
sudo mount -t ext4 /dev/sda1 /mnt
sudo touch /mnt/empty_file
sudo blkid -p /dev/sda1
```

---

### Post by kiran88pnjr on 2010-02-19
> **nuwave said:**
> you seem to be having the same issue i had though there is a slight difference in your error message but here is how I got help to fix my problem

[http://ubuntuforums.org/showthread.php?t=1397193](http://ubuntuforums.org/showthread.php?t=1397193)

read the entire thread to make sure you have the same problem and the final solution is on the last page posted by meierfra

meierfra's page says to Download util-linux-ng-2.17.tar.gz to your Desktop. How can I do that since I can't even access to login screen ?

And ask him to help me too

---

### Post by amsterdamharu on 2010-02-20
The post mentioned above tells you to zero out your partition table, if you don't have ext4 it will destroy all data on that partition. Here are the commands you should type and post the response. 

The solution is in there but just a bit down the posts.

```
sudo fdisk -l
sudo more /etc/fstab
sudo mount -t ext4 /dev/sda1 /mnt
sudo touch /mnt/empty_file
sudo blkid -p /dev/sda
```

Please tell us what you get when you run sudo more /etc/fstab as mentioned twice before we need to see what partition is related to that uuid.

[update]by the way, changing the fstab to use /dev/sd?? (where ?? are disk and partition) would solve it too since the uuid is not recognized. [update]

---

### Post by nuwave on 2010-02-20
cant you run the LiveCD(or LiveUSB)? I ran a LiveUSB for my netbook and I fixed it my issue inside the LiveUSB try that and give the commands that amsterdamharu posted. Also post any output that get so we can know what going on with your system

---

### Post by kiran88pnjr on 2010-02-20
> **amsterdamharu said:**
> The post mentioned above tells you to zero out your partition table, if you don't have ext4 it will destroy all data on that partition. Here are the commands you should type and post the response. 

The solution is in there but just a bit down the posts.

```
sudo fdisk -l
sudo more /etc/fstab
sudo mount -t ext4 /dev/sda1 /mnt
sudo touch /mnt/empty_file
sudo blkid -p /dev/sda
```

Please tell us what you get when you run sudo more /etc/fstab as mentioned twice before we need to see what partition is related to that uuid.

[update]by the way, changing the fstab to use /dev/sd?? (where ?? are disk and partition) would solve it too since the uuid is not recognized. [update]


I've done it using the rescue shell And problem solved. Thanks everyone.

:D:D:D:D:D

---

### Post by nuwave on 2010-02-21
good to hear

---

