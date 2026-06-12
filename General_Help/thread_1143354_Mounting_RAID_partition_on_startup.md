---
title: "Mounting RAID partition on startup"
date: 2009-04-29
forum: General Help
---

### Post by linuxuser21 on 2009-04-29
I have followed [this]("http://www.psychocats.net/ubuntu/mountlinux") tutorial and successfully made my IDE hard drive mount on startup with correct permissions.  (Thanks Psychocats!)  I've tried to do the same for the RAID partition.  Only, cciss/c0d0p8 instead of /sda and I just get errors.
```
mkdir: cannot create directory `/cciss/c0d0p8': No such file or directory
```
&
```
mount: mount point /cciss/c0d0p8 does not exist
```

---

### Post by fjgaude on 2009-04-30
> mkdir: cannot create directory `/cciss/c0d0p8': No such file or directory

I'm sure you can do this... where is /cciss?

If it already exist then move there and then create /c0d0p8.

---

### Post by linuxuser21 on 2009-04-30
It's in /dev.
instead of a normal hard drive: /dev/sda, it's /dev/cciss/c0d0p8.

---

### Post by fjgaude on 2009-04-30
I must admit I'm not sure what you have... raid, I don't see it. If it's raid then it's hardware raid, from a card or the like, and you need a driver to mount the array first, before you can see it.

What is this /dev/cciss, please?

Anyway, make a mountpoint somewhere on your boot drive, e.g., /home/raid then you can mount the partition as needed.

```
sudo mkdir /home/raid

sudo mount /dev/cciss /home/raid
```

That might do what you wish.

---

### Post by linuxuser21 on 2009-04-30
Yes, it's hardware RAID.  If you look at my signature, I have 3 72.8gb SCSI drives with a HP Smart Array 641 controller (set up as RAID 5).  Of course this means that the computer picks it up as 1 logical drive.  In the screenshot I have attached, you can see that I have it partitioned it so I have a 90gb partition by itself.  (I didn't just leave the rest as a /home partition.  I wanted to have it as extra space for my personal files or possibly other distros, OSs, ect., in the future.)
I have Ubuntu installed on the array and everything works as it should.  My focus right now is to make the 90gb partition mount on startup with the correct permissions as I was able to do with the IDE HDD.  I am able to mount it by clicking on it under the "Places" menu or from the sidebar.

---

### Post by linuxuser21 on 2009-05-01
> **fjgaude said:**
> ```
sudo mkdir /home/raid

sudo mount /dev/cciss /home/raid
```

It worked!
For future reference, I used these codes:
```
sudo mkdir /disk

sudo mount /dev/cciss/c0d0p8 /disk
```
In fstab:
```
/dev/cciss/c0d0p8 /disk ext4 defaults 0 0
```
```
sudo chown -R <username>:<username> /disk

sudo chmod -R 777 /disk
```
Thank you fjgaude!

---

### Post by fjgaude on 2009-05-01
Great! So much to consider with each setup... few are the same. I had no knowledge of your HP controller, or whatever.

Anyway, we all learn something new each day.

---

