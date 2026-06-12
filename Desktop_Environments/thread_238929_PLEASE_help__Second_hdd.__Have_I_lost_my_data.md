---
title: "PLEASE help:  Second hdd.  Have I lost my data?"
date: 2006-08-18
forum: Desktop Environments
---

### Post by betty on 2006-08-18
Dear All:

Any help would be very much appreciated!  

I recently added a second hard drive to my ubuntu-only box.  Searching these forums gave me some answers on how to access that drive.  I don't remember exactly what I did, but I do remember formatting ext3, creating a directory /backup, typing chmod to edit permissions or something, and then the drive was accessible.

My problem:  I moved a whole bunch of VITAL data from my external HDD to the /backup hdd in my computer.  It copied well, it was accessible, no problem, and I deleted that data off my external hdd, leaving it on my new internal disk.

The next time I rebooted, the drive was not accessible again.  I get:  

Unable to mount the selected volume
error: device /dev/hdc1 is not removable

error: could not execute pmount

Again searching through the forums, I followed some other instructions that somehow screwed up root permissions and the entire OS, and made me need to reinstall ubuntu altogether.  I still find myself with the same problem of accessing that drive, and although I think the data is sitting there somewhere, I don't know how to access it!

Can anyone give me a step by step of how to do this, WITHOUT losing the data that I already copied on to the drive in the /backup folder that used to exist?  Although I use only ubuntu, I am still a novice working with the terminal.  Please help if you can!  

Much appreciated!
Betty

---

### Post by waldschm on 2006-08-18
Have you tried mounting the second drive from the command line after boot? For example:

sudo mkdir /media/backup
sudo mount -t ext3 /dev/hdc /media/backup

I think part of the problem could be coming from the pmount command usage rather than just using mount. See if you are able to mount it like this.

---

### Post by gerbman on 2006-08-18
Let's start at the beginning. Please post the contents of your /etc/fstab file, as well as any information you have about the hard drive (IDE/SATA, partition layout, etc.)

---

### Post by jimbren on 2006-08-18
I'm not at my linux box right now, so I can't promise that these instructions are exactly right, but they should be harmless.

At a command prompt, do the following:
```
fdisk -l
```

this should list the partition information for all of your drives, including the external. 

From there, you should be able to mouunt the drive manually or add a line to fstab that will mount the drive automatically upon boot.

If you modify your fstab file, be sure to back it up first.  After making the change, reload fstab by doing this:

```
sudo mount -a
```

Let me know how that works out.

---

### Post by betty on 2006-08-18
Ok thank you.  I'm at work now, but I'll try everything that people suggested tonight, and report back.

Sincerely,
betty

---

### Post by waldschm on 2006-08-18
A little further reading on pmount makes things a little clearer (man pmount). It appears your second hard drive is not in your fstab and ubuntu is therefore treating it as a removable device to be mounted with pmount. Since it isn't a removable device the pmount command fails. So yes, post your fstab; an entry will probably need to be added for the new hard drive.

---

### Post by betty on 2006-08-18
Dear All:

Here the output of fdisk -l


Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1       14593   117218241    5  Extended
/dev/hda5   *           1          31      248944+  83  Linux
/dev/hda6              32       14593   116969233+  8e  Linux LVM

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1        9447    75882996   83  Linux
/dev/hdb2            9448        9729     2265165    5  Extended
/dev/hdb5            9448        9729     2265133+  82  Linux swap / Solaris

When I type:   sudo mount -t ext3 /dev/hdb /media/backup
I get:  mount: /dev/hdb already mounted or /media/backup busy

Again, I see the drive in Nautilus, but when I click on it, I get "Unable to mount the selected volume:  error:  device /dev/hdb1 is not removable, error:  could not execute pmount

What do I do?

Thanks!!
betty

---

### Post by waldschm on 2006-08-18
What's your output from fdisk -l?

---

### Post by betty on 2006-08-18
Sorry about that, what is listed above IS the output of fdisk -l

---

### Post by dannyboy79 on 2006-08-18
Try adding the number of the partition that you want mounted to your arguement, so sudo mount -t ext3 /dev/hdb1 /media/backup. If that doesn;t wotk tell us what your fstab looks like. You could try to add a line to your fstab and then do sudo mount -a and it will try to mount everything in your fstab.

---

### Post by dannyboy79 on 2006-08-18
Also, is the folder you are trying to mount it to owned by you? sudo chown "enter username here" /media/backup? Then what about he folders read write permissions? What are those? This is interesting to me because this has happened to me but I forgot what I did to resolve it? Sorry I can't give you a straight away answer

---

### Post by betty on 2006-08-18
Ok, great it works.

Now when I go to /media/backup, my files are there.

But, still when I click on the hdd icon from nautilus, it still doesn't work.  I navigate to the directory from the terminal, or from nautilus...

Preferably, I'd like to click on the drive and have the structure appear like in windows... but if that is not possible, how do I keep it permanently mounted?

It's little things like this that should be a bit easier in linux...  just the same, the benefits outweigh the woes.

Thanks for your help again, 
betty.

---

### Post by waldschm on 2006-08-19
To get it to moung automatically you have to add it to your fstab file. Open this file with:

```
sudo gedit /etc/fstab

```
or whatever text editor you prefer and add a line like this

```
/dev/hdb1       /media/backup     ext3    defaults        0       2
```

---

### Post by jimbren on 2006-08-19
I've had a very similar setup in the past, and I thought it was a little cleaner and more convenient to have my backup folder outside of /media.

So I made a directory off of root for my backups and chowned it:
```
sudo mkdir backups
sudo chown username:username backups
```

And then in my fstab folder, it looked almost like the comment from waldschm, with modification for the mount point:

```
/dev/hdb1       /backups     ext3    defaults        0       2
```

Hope this helps....

---

### Post by betty on 2006-08-20
It did help.  Thanks!

---

