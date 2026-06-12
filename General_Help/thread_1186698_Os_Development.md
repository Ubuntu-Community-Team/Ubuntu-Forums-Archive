---
title: "Os Development"
date: 2009-06-13
forum: General Help
---

### Post by hahnski07 on 2009-06-13
I am developing my own operating system.  I just recently moved from Vista to Ubuntu :).  When I was on windows I used VFD(Virtual Floppy Drive) to create a FAT12 drive and put my OS on it.  Bochs booted from this just fine.

On Ubuntu there is no VFD(I tried using it with WINE to no success).  I have created a FAT12 virtual floppy drive with mkdosfs and successfuly mounted it.  Ubuntu recognizes it and I can add/remove files from it.  However, i cannot get Bochs or QEMU or VirtualBox to boot from /dev/fd0 or /media/floppy0.

I have also tried making a .img file from the drive using 
```
cat /dev/fd0 > image.img
```as suggested on this site: [http://untitledfinale.wordpress.com/2007/10/09/create-mount-and-copy-floppy-disks-images-under-linux/](http://untitledfinale.wordpress.com/2007/10/09/create-mount-and-copy-floppy-disks-images-under-linux/)

Thanks for your help

---

### Post by synapsys on 2009-06-13
[http://en.wikipedia.org/wiki/Dd_(Unix)]("http://en.wikipedia.org/wiki/Dd_%28Unix%29")

---

### Post by hahnski07 on 2009-06-13
thanks for the quick reply but...

```
administrator@Administrator-Laptop:~$ sudo dd if=/dev/fd0 of=/flopp.img bs=512 count=2880
[sudo] password for administrator: 
dd: reading `/dev/fd0': Is a directory
0+0 records in
0+0 records out
0 bytes (0 B) copied, 0.00137224 s, 0.0 kB/s
administrator@Administrator-Laptop:~$ 

```

---

### Post by baxzius on 2010-06-29
Its good making your own operating system. i really appreciate.
i am also doing current task.

not look how i am compiling my Os.
look when you compile your kernel you may get resulting image file withextension .img.
it may be a floppy image file.

[B]IN QEMU
to run the result image in qemu... you can enter the following command.[/B]

$ qemu -fda os.img

[B]if you wanna add some files in it.... then you have to play the game. its like this.
[/B]
$losetup /dev/loop0 os.img
$mount -t vfat /dev/loop0 /mnt/mydir

[B]then adding files into /mnt/mydir automatically goes to the file os.img.
and to deactivate the file.. you just enter 2 commands.[/B]
$umount /mnt/mydir
$losetup -d /dev/loop0

---

