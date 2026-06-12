---
title: "Creating ISOs"
date: 2006-09-25
forum: Desktop Environments
---

### Post by Rhapsody on 2006-09-25
I've recently found that creating ISOs of some of my CDs would Dead Handy™, as my DVD drive is extremely noisy when reading (Dynamic Damping System? Noise-control System? Yeah, right.) and I can lose just about anything in this room.

The problems is that I don't seem to be able to figure out an easy way to do this on Kubuntu. Any ideas?

---

### Post by pay on 2006-09-25
To create an iso from a CD/DVD, open up the terminal and type```
sudo umount /dev/cdrom
dd if=/dev/cdrom of=file.iso bs=1024
```Obviously change /dev/cdrom to the location of your cdrom.

To create an iso from a folder type```
mkisofs -o file.iso /location_of_folder/
```

---

### Post by Rhapsody on 2006-09-26
That resulted in:

```
dd: reading `/dev/cdrom': Input/output error
26848+0 records in
26848+0 records out
Segmentation fault
```

The ISO produced is 26.2MB, which I'm not convinced is a full ISO as the CD contains 7 sizable audio tracks along with the data track.

---

### Post by pay on 2006-09-26
Change /dev/cdrom to your cdrom drive. For example mine is at /media/cdrom0

---

### Post by Rhapsody on 2006-09-26
> **pay said:**
> Change /dev/cdrom to your cdrom drive. For example mine is at /media/cdrom0
Same here. But that just creates a zero-byte file:

```
dd: reading `/media/cdrom0': Is a directory
0+0 records in
0+0 records out
%<PRIuMAX> bytes ((null)) copied, 0.000704 seconds, 0.0 kB/s
```

It doesn't even seem to care if it's mounted or not. It just creates zero-byte files over and over.

---

### Post by pay on 2006-09-26
Sorry I told you the wrong thing:???: 
Open up your fstab file ```
nano /etc/fstab
``` and see what device cdrom is (do know edit it unless if you know what you are doing) and then use that instead. For example mine is at /dev/hda so I typed in```
dd if=/dev/hda of=file.iso bs=1024
```

---

### Post by Rhapsody on 2006-09-26
/dev/hdc points to my DVD drive, but the results of using that are the same as with /dev/cdrom.

```
dd: reading `/dev/hdc': Input/output error
26848+0 records in
26848+0 records out
Segmentation fault
```

I don't see to be getting the audio tracks at all.

---

### Post by pay on 2006-09-27
Maybe the disc is faulty.

---

