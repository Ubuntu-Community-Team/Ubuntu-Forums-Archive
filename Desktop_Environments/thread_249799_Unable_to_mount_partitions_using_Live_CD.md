---
title: "Unable to mount partitions using Live CD"
date: 2006-09-03
forum: Desktop Environments
---

### Post by Rhapsody on 2006-09-03
I've been trying to mount some of my partitions from an Ubuntu Live CD (to copy data and more easily do stuff with GParted) but for some reason, I seem totally unable to mount any partitions.

Going into 'Places', 'Computer' and attempting to access any of my partitions results in an "Unable to mount the selected volume" error. Under 'Further details', I get "error: device [etc] is not removable" and "error: could not execute pmount".

GParted simply gets stuck at "Scanning all devices..." and after some CD and HD activity, nothing happens.

The drives will mount just fine in regular operation, but the Live CD seems totally incapable. I'm probably not doing something that I should be doing, but I've no idea what.

---

### Post by dbasis on 2006-09-03
create an device (in german: ordner) for example /mnt/harddisk
then "sudo mount /dev/hda6 /mnt/harddisk

now u should be able to get to that harddrives even in live cd;it at least worked out at mine pc

---

### Post by Rhapsody on 2006-09-03
> **dbasis said:**
> create an device (in german: ordner) for example /mnt/harddisk
How do I do that?

---

### Post by Rhapsody on 2006-09-03
Still don't really have a solution that I can understand here...

---

### Post by varean on 2006-09-03
```

sudo mkdir /mnt/harddisk
sudo mount /dev/hda6 /mnt/harddisk

```

This creates a directory where you can mount your partitions, in this example, /dev/hda6, choose another partition based on what you want to mount.  Try "fdisk -l" to see the partitions you have.

---

### Post by Rhapsody on 2006-09-03
> **varean said:**
> This creates a directory where you can mount your partitions, in this example, /dev/hda6, choose another partition based on what you want to mount.  Try "fdisk -l" to see the partitions you have.
Alright, and this would let GParted do its stuff with the partitions? Because I have a rather lengthy plan of what I intend to do with this.

1) Shrink NTFS partition at the start of my second from 248GB to 100GB.
2) Create a new ext3 partition from the free space in the middle of my second drive.
3) Mirror data from NTFS partition to the ext3 partition.
4) Delete the NTFS partition.
5) Create new ext3 partition at the start of my second drive from the free space now left.
6) Mirror data from the ext3 partition in the middle of drive to the one at the start of my second drive.
7) Delete the ext3 partition in the middle of my second drive.
8) Extend the ext3 partition at the start of second drive to fill all available space.
9) Copy any data I want to keep from the FAT32 and /home partitions on my first drive that I want to keep to the new ext3 partition on my second drive.
10) Reboot to Kubuntu install CD, wipe the entire first drive and start from scratch.
11) New Age Of Kubuntu.

I'm starting to obsess over the details of this plan, but it's a big one and it really all has to work in one go or it won't work at all.

---

### Post by bulldog on 2006-09-03
I should think this over again.
It seems to me there must be a simpler way to acomplise that.:p

---

### Post by Rhapsody on 2006-09-03
> **bulldog said:**
> I should think this over again.
It seems to me there must be a simpler way to acomplise that.:p
Seems about the simplest way to me. Someone once said GParted could extend partitions backwards (which would eliminate a lot of steps), but that sounds like nonsense to me.

Once I'm done, I'll only have three partitions and a swap partition left. It's just the path there that's a bit complicated and hairy.

The problem is really me. My confidence is fairly low, and most problems with Kubuntu can be traced back to me (quite a change from Windows).

---

