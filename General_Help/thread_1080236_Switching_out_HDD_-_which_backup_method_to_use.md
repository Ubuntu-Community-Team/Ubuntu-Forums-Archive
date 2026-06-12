---
title: "Switching out HDD - which backup method to use?"
date: 2009-02-25
forum: General Help
---

### Post by sirsmegalot105 on 2009-02-25
Hi,

I'm changing the HDD in my Acer laptop from 120GB to 320GB, the trouble is I'm not sure which if the many types of backup methods mentioned on this forum to use. Hopefully someone can help :)

I looked at Part Image but it says it doesn't to a good job of restoring image files to larger partitions than the original. I have a dual boot system but have my own separate image file and program for restoring the Windows partition, once the HDD is replaced.

Here are my partitions:

[IMG]http://img511.imageshack.us/img511/2312/screenshotdevsdagparted.png[/IMG]

All I want to backup at the / and /home partitions - preferably in an image file. However....

1) When I re-partition the new 320GB HDD with larger partitions than previously (but similar setup), will this "break" if the partition sizes are not the same anymore? (and swap may have different sda name / be larger etc?)

2) If I use the compression tar file method for the two partitions, again, will this ensure everything I had previously was restored to the new HDD?

3) Would I be better off just backing up my /home (separate partition) and fresh installing 8.10 - would that restore all my old programs, settings, customisations or will I need to do further things?

Thanks in advance for the help

---

### Post by geirha on 2009-02-25
I think the easiest way is to create images of your ext3 partitions with dd. I'll assume you are booted with the ubuntu CD, and have an external drive connected to store the images on. Replace /path/to/save/images with the proper path (/media/disk probably)
```

sudo dd if=/dev/sda7 of=/path/to/save/images/root.img
sudo dd if=/dev/sda8 of=/path/to/save/images/home.img

```

That will take quite a long time, since it copies the entire partitions, including the free space. Don't bother with the swap partition, just create a new one with a new filesystem. You'll need to change the swap entry in /etc/fstab to reflect the new swap partition's UUID. More on that later.

You can then restore those images to any partition that is the same size or larger than the previous partitions. This copies the entire filesystems on the partitions, and the filesystems has a size, which by default is the same size as the partition they were created on. If you copy a filesystem to a partition that is larger than the filesystem, the filesystem's size will not automatically be larger, it will be 14.65 GiB for your / partition still. You can however use the resize2fs command to resize the filesystem to fill the entire partition.

I'll assume you now have replaced the old harddrive with the new harddrive, and have booted with the ubuntu CD again, so that the new harddrive will now be /dev/sda.

With that in mind, create two new partitions for / and /home, using gparted, on the new harddrive, make sure they are greater or equal to the size of the previous partitions. I'll just assume the two partitions are /dev/sda1 and /dev/sda2 for / and /home respectively on the new harddrive.
```

[color=red]# Make sure the two devices (/dev/sda1 and /dev/sda2 in this example)
# are the ones you just created. It will wipe everything that may be
# contained on those partitions before you run this.[/color]
sudo dd if=/path/to/save/images/root.img of=/dev/sda1
sudo dd if=/path/to/save/images/home.img of=/dev/sda2
# Grow filesystems to use all space of the partition
sudo resize2fs /dev/sda1
sudo resize2fs /dev/sda2

```

Now create a new swap partition on the new drive with gparted, then find the new UUID (assuming the swap is /dev/sda3), mount your new / partition, edit /etc/fstab and replace the swap entry's UUID with the new one.
```

sudo blkid /dev/sda3          # copy the UUID it outputs
sudo mount -v /dev/sda1 /mnt
sudo nano /mnt/etc/fstab      # change the UUID and save
sudo umount -v /dev/sda1

```

Lastly, you need to install grub on the new hard drive
```

sudo grub # Starts a grub shell. The following commands should be run in that grub shell
grub> find /boot/grub/stage1 # Find the partition where grub's files are stored
                             # Most likely it will output (hd0,0). Whichever it is,
                             # Use it in the next command
grub> root (hd0,0)
grub> setup (hd0)            # Installs grub on the MBR
grub> quit

```

Reboot ...

I have no idea how to copy the NTFS partitions and still have windows work. You'll need to ask in a windows forum for that.

Hope this wasn't too technical, and I haven't tried this myself, but I see no reason why it shouldn't work. And if it fails, your old hard drive should be unaffected by all this, so you that you can try again with perhaps a different approach. Feel free to ask if you don't understand exactly what I mean or what a command does.

---

### Post by sirsmegalot105 on 2009-02-25
Thanks for the detailed reply :)

The only problem I can see at the moment is that my external USB drives are FAT32 formatted and I can't change this (since there's a lot of data on them).

Is there an option to do this without it backuping up the free space? I can see why it has to do it though, don't get me wrong.

---

### Post by geirha on 2009-02-25
Well, you could boot the Ubuntu CD and shrink the two partitions as much as possible, so that there is 0 bytes left on those filesystems, or at least get the size down to below 4GiB, which is the maximum filesize on FAT32. When resizing partitions you always run a small risk of something going wrong, so make sure you backup the data you can't afford to lose first.

EDIT: 
Oh and, the free space may contain random data or lots of zeroes. The latter would compress very well, so just compressing the images might also do the trick, but I think it most likely contains random data. I'll just show how to compress the image from dd anyway.

```
dd if=/dev/sda7 | gzip >/path/to/save/images/root.img.gz
```

The reverse of that would be
```
zcat /path/to/save/images/root.img.gz | dd of=/dev/sda1
```

---

### Post by sirsmegalot105 on 2009-03-02
Thanks for your help geirha - got it all sorted :)

---

