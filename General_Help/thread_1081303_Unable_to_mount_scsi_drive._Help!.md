---
title: "Unable to mount scsi drive. Help!"
date: 2009-02-26
forum: General Help
---

### Post by phr33k-dc on 2009-02-26
I have installed ubuntu over vista. my laptop is made up of a c drive and a d drive. I wrote over vista on c drive and under Computer in ubuntu i cant mount tne d drive and dont know why. any ideas? badly need help or i cant use 300GiG........

---

### Post by taurus on 2009-02-26
What filesystem is the "d" drive?  You probably just have to mount it before you can use/access it.  Open a terminal and post the outputs of these commands.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
sudo blkid
cat /etc/fstab
df -h
```

---

### Post by phr33k-dc on 2009-02-26
Dont know what you mean. i think its labaled as 'swap'. Count mount

---

### Post by phr33k-dc on 2009-02-26
This means i cant access 300GiG!!!!

---

### Post by sanemanmad on 2009-02-26
> **phr33k-dc said:**
> Dont know what you mean. i think its labaled as 'swap'. Count mount

Please post the contents of each command [taurus ^ has provided]. You will need to execute each line individually in the Terminal.

---

### Post by phr33k-dc on 2009-02-26
Foe the first command by taurus alot of things came up and at the end it said 'Disk /dev/sdb doesn't contain a valid partition table'

---

### Post by sanemanmad on 2009-02-26
> **phr33k-dc said:**
> Foe the first command by taurus alot of things came up and at the end it said 'Disk /dev/sdb doesn't contain a valid partition table'

okay, lets do this instead, after each command add 

sudo fdisk -l > ~/Desktop/fdisk.txt 

sudo blkid > ~/Desktop/nextcommand.txt 
and so on. 

This way you can upload these as attachments and we can look at them.

---

### Post by phr33k-dc on 2009-02-26
Im very bad at this can tell me exactly wat to type in termial? im in a bit of a frenzy since i spent a fortune on this laptop.......

---

### Post by phr33k-dc on 2009-02-26
besides i tryed the first command there and it just said the same thing.

---

### Post by sanemanmad on 2009-02-26
ok, in a terminal type in:
```
sudo fdisk -l > $HOME/Desktop/fdisk.txt
```
```
sudo blkid > $HOME/Desktop/blkid.txt
```
```
cat /etc/fstab > $HOME/Desktop/fstab.txt
```
```
df -h > $HOME/Desktop/df.txt
```

Then right before you post these files, reboot then open a terminal type 

```
sudo cat /var/log/messages|grep sd > $HOME/Desktop/sd.txt
```

---

### Post by phr33k-dc on 2009-02-26
there in the order of the commanda i think

---

### Post by phr33k-dc on 2009-02-26
last one cause was to big

---

### Post by phr33k-dc on 2009-02-26
no its too big a file (exceeds forum limit

---

### Post by phr33k-dc on 2009-02-26
My laptop has a total space of around 600 GiG

---

### Post by sanemanmad on 2009-02-26
Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8bdab79b

That is your hdd, ubuntu is seeing it, just doesnt know what it is. So if there is data you need on here then you should back it up, [not my cup of tea] otherwise format it and mount it in fstab. You can look here for how to format and mount etc... [https://help.ubuntu.com/community/DrivesAndPartitions]("https://help.ubuntu.com/community/DrivesAndPartitions")

---

### Post by phr33k-dc on 2009-02-26
No dont worry its completely blank but could you tell me what to look for on the site?

---

### Post by phr33k-dc on 2009-02-26
I can use my c drive just fine and that has everything on it but cant get at the d drive (half of complete space)

---

### Post by phr33k-dc on 2009-02-26
this might help

---

### Post by phr33k-dc on 2009-02-26
in fact that might tell you the problem would it?

---

### Post by sanemanmad on 2009-02-26
Follow this guide on how to format using gparted. [Mounting a parition]("http://www.psychocats.net/ubuntu/mountlinux")

---

