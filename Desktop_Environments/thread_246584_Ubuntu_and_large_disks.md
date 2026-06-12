---
title: "Ubuntu and large disks"
date: 2006-08-29
forum: Desktop Environments
---

### Post by nnigam on 2006-08-29
I am using Ubuntu for the last few weeks, and it is really very good. No problem in doing things that I normally do, and wireless is trivial with it. However, I do have one problem. Ubuntu does not recognize my large disks, and those it recognizes, it cannot mount. I get an error saying, 

   error : device /dev/hda1 is not removable
   error : could not execute pmount

I also tried this with Suse and had the same problems. Knoppix seems to be the only one that can see the drives fine and mount them. Because of this I cannot install to HD.

Any idea on what to do about this?
Thanks
Neeraj

---

### Post by kaamos on 2006-08-29
Hello!

Have you already tried installing with the alternative (text-based) install cd?

---

### Post by nnigam on 2006-08-29
Not yet. I want to make sure I can get to my hard disk in case something happens before I start putting stuff there. 

I have tried this on several pc with the same results. Could there be some limit to size of the disks, LBA settings in bios, maximum cilinders etc. I remember many years ago, we had to make some setting in the bios to get disks to be identified on the pc.

Thanks
Neeraj

---

### Post by kaamos on 2006-08-29
To me the pmount error just looks like the disk is not configured to be mounted. By clicking on the image in nautilus pmount tries to mount it as a removable drive which can't be done for security reasons.

Try accessing the drive through System->Administration->Disks

---

### Post by nnigam on 2006-08-29
Makes sense. But what if I want to access data on my fat32 or ntfs partitions at least in read only mode.

I tried this just now. In disk manager, the device shows up as inaccessible. Clicking the enable button does not do anything. I will try this on other pc's tonight.



thanks
Neeraj

---

### Post by Sam on 2006-08-29
I don't know if it'll work, but install the kernel which is appropriate to your computer architecture (ie. don't use the i386 but i686 or k7)

---

### Post by fluffnik on 2006-08-31
> **nnigam said:**
> Makes sense. But what if I want to access data on my fat32 or ntfs partitions at least in read only mode.

I tried this just now. In disk manager, the device shows up as inaccessible. Clicking the enable button does not do anything. I will try this on other pc's tonight.


Have you specified a mount point, and does it exist?

You could try this in a terminal:
[LIST=1]
[*]```
sudo mkdir /mnt/hda1
``` which will create a mountpoint.
[*]```
sudo mount -t vfat -o uid=1000 /dev/hda1 /mnt/hda1
``` which should mount the disk as belonging to the default user.
[/LIST]

If you want to automate this a glance at man fstab may help.

---

