---
title: "Welland ME-601J eSATA"
date: 2009-01-16
forum: General Help
---

### Post by charonred on 2009-01-16
I just bought a Welland ME-601J eSATA/USB HDD docking station - it comes with drivers for Win 98SE/ME/2000/XP/Vista and for Mac OS 9.0 or above, but their is no mention of anything for Linux (no surprise there).

I'm using a AM2+ Gigabyte MA790FX-DS5 mainboard, AMD 2.8Ghz Dual Core CPU with 2 GB RAM. I've used all available SATA ports inside, so I thought I'd make use of the eSATA ports.

I have a brand new WD 500 GB SATA HDD in the Welland docking station connected via the eSATA cable, and running it's own power supply.

I'm running 8.04.1 Hardy, and the drive shows as a SCSI in 'Computer', but I'm unable to mount it - as yet I haven't partitioned/formatted it, that was first job I intended doing once in Ubuntu.

I want to be able to 'hot swap' different drives for storage, and occasionally boot a different OS via eSATA HDD.

Anyone had experience with setting these up to run under Ubuntu ?

---

### Post by FIONEX on 2009-01-16
How do you a mount a drive that has no file system?  You need partition and format first my friend...
Also, it doesn't need to be mounted to be partitioned using "parted"

---

### Post by cariboo on 2009-01-16
I have several eSata drives, they work exectly like a normal Sata drive, except they are hot pluggable. Just plug the drive in and use System-->Administration-->Partition Editor to partition and format the drive. If you haven't got the Partition Editor entry in your menu, install gparted.

Jim

---

### Post by charonred on 2009-01-17
Yeah, I was thinking that, and figured Part Ed would sort it - but Part Ed wasn't displaying that drive in list, only existing 4 SATA & 1 PATA as /dev/sda,sdb,sdd,sde,sdf

Rebooted PC a couple of times and now lists as /dev/sdc in Part Ed, so have partitioned as primary and formatted to ext3; but now isn't showing in 'computer' (showed as SCSI before), so might reboot and see what happens

---

### Post by FIONEX on 2009-01-17
You can try manually mounting it once using the terminal. OR follow these steps to add it to the /etc/fstab file so that it automounts.

Create a new directory under /media and give it a name.  Let's suppose it's called "newdrive".  Type this in a terminal to create it:
```

sudo mkdir /media/newdrive

```

open your fstab by typing this in a terminal:
```

sudo gedit /etc/fstab

```

add the following line and change "new drive" to whatever you called the directory above.  Save and close gedit.
```

/dev/sdc1 [COLOR="Red"]/media/newdrive[/COLOR]               ext3    noatime,errors=remount-ro 0       1

```


On the next reboot, it'll automount.  But to mount it right away, run the following in a terminal!
```

sudo mount -a

```

---

### Post by charonred on 2009-01-17
Hmm, after reboot the esata drive now shows in 'Computer' as '500.1 GB Media', but if I try to rename it I get the following dialogue

> **The item could not be renamed.**
Sorry, couldn't rename "500.1 GB Media" to "eSATA-WD500": Operation not supported by backend

Not super important, but if I add another eSATA of same size, then I'll need to differentiate between them.

Just going over all drives; apart from my Hardy install (ext3), all other drives are formatted to NTFS so I can access them when in Windoze. But when formatting in Part Ed, the NTFS option is greyed out; I only have ext 2 & 3, fat16 & 32, linux-swap,and reiserfs available; is this normal for an eSATA drive ?

---

### Post by charonred on 2009-01-17
On looking at the properties of the new drive, there is 23.5 GB used, and a folder inside called 'lost and found' and when I click displays the following
> **The folder contents could not be displayed.**
You do not have the permissions necessary to view the contents of "lost+found".

---

### Post by cariboo on 2009-01-17
That is normal, you can delete Lost+Found, the 23.5Gb  used is the 5% reserved for root, and for journaling. You can use tune2fs to reduce the reserved hard drive space, for more info have a look at:

```
man tune2fs
```

Tune2fs is installed by default.

Jim

---

### Post by charonred on 2009-01-17
It won't let me delete it cause I don't have the correct permissions ??

Anyhow, even though I've been living in Linux-Land for the past 6 months, I still need to format it as NTFS so it's readable when I occasionally need to use Windoze (why does Part Ed have NTFS greyed out). 

Is Part Ed the same as GParted, and if not, can I install GParted as well and use that to format the drive to NTFS?

---

### Post by charonred on 2009-01-25
Used a live boot disc with GParted on it, formated esata drive to NTFS, so now it works with Windows as well

---

