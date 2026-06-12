---
title: "Gparted question"
date: 2006-07-25
forum: Desktop Environments
---

### Post by jordilin on 2006-07-25
I have an external hard drive connected by usb. I'm going to format and partition it by using Gparted. Ubuntu mounts the hard drive automatically. Have I to unmount it in order to work with Gparted? If I don't unmount the hard drive I can't do any partition. Is this the procedure??

---

### Post by nebc on 2006-07-25
My understanding is that mounting a drive means you can do stuff to it such as read/write/execute.  If you don't mount it, it's as if it's not there.  Thus, you need it mounted to use gparted.

The thing you can't do with gparted (and I think this is what you were getting at) is reformat the drive that has the current opearting system on it.  This is why you can reformat your drive when you boot from a CD/disk but not when you've booted from the drive itself.

---

### Post by jordilin on 2006-07-25
> **nebc said:**
>  This is why you can reformat your drive when you boot from a CD/disk but not when you've booted from the drive itself.

When you boot from a live CD it does not mount your internal drives automatically, so they must be unmounted in order to partition them. So, the most probable thing, is that hard drives must be unmounted in order to format and partition them if using GParted.

---

### Post by endfx on 2006-07-25
You are correct. You cannot partition a mounted drive.
Here is what I would do:

1. Run the command "mount" from the command line.
   This will tell you what device the usb hard drive is.
    (should be something like /dev/sda1)

2. unmount the usb harddrive

3. open gparted and partition the device name you found in step one. Example: /dev/sda1

Does this answer your question?

---

### Post by jordilin on 2006-07-25
> **endfx said:**
> You are correct. You cannot partition a mounted drive.
Here is what I would do:

1. Run the command "mount" from the command line.
   This will tell you what device the usb hard drive is.
    (should be something like /dev/sda1)

2. unmount the usb harddrive

3. open gparted and partition the device name you found in step one. Example: /dev/sda1

Does this answer your question?
That is what I wanted to hear. So, I was not wrong. I was not sure but I see that I'm not the only one. Now, the technical question. Why the harddrive must be unmounted in order to do a partition or a format with gparted?

---

### Post by endfx on 2006-07-26
I'm not sure if my answer will be technical enough for you, but I'll try to give a good answer.

1. For a drive to be partitioned or formatted, it must be unmounted
   not only for gparted, but for any partitioning program (fdisk, cfdisk, etc). So requirement is not something unique to gparted.


2. When you partition a harddrive you are changing the logical structure of the disk. That is, you are changing how the operating system sees and uses the disk. 
- If a disk is mounted, that means things can be read and written on the disk.

- So imagine you are downloading a huge file from the internet. The operating system is sending bytes to the disk to be written on the disk. Now all of a sudden, along comes gparted and changes the logical structure of the disk (during your download). Now the operating system sees the disk differently. If the file continues to download and be written to this newly partitioned disk, there is a good chance the file would be corrupt. Bytes for the file you are downloading may be in different partitions, which means the filesystem is not in tact. It is just one big mess.

So basically, you must unmount a drive for it to be partitioned so no other activities are happening on the disc while you are partitioning the disk.

Does this answer your question?

---

