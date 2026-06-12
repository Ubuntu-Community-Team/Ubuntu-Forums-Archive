---
title: "Swap space not being used"
date: 2012-07-06
forum: Desktop Environments
---

### Post by jroa on 2012-07-06
I had several Linux distros installed on several partitions not very long ago.  I decided to clean house and deleted everything except Ubuntu.  Now, I have a 133GB logical partition for Ubuntu and 8GB for swap.  

However, when I run free -m, it shows that I do not have any swap memory, just physical memory.  I probably accidentally deleted the swap space that Ubuntu was using.

Is there a way that I can manually tie Ubuntu to this swap space, or do I need to reinstall?

Here is the output for free -m:

```
             total       used       free     shared    buffers     cached
Mem:          3016       2760        256          0         73        768
-/+ buffers/cache:       1917       1098
Swap:            0          0          0

```

and here is the output for parted and print:

```
Model: ATA Hitachi HDP72505 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  525MB  524MB   primary   ext4
 2      526MB   358GB  358GB   primary   ntfs            boot
 3      358GB   500GB  142GB   extended                  lba
 6      358GB   492GB  133GB   logical   ext4
 5      492GB   500GB  8472MB  logical   linux-swap(v1)

```

---

### Post by plucky on 2012-07-06
Open a terminal and post output for ```
cat /etc/fstab
sudo blkid
cat /etc/initramfs-tools/conf.d/resume
```


Your swap partition is not being mounted.

---

### Post by SeijiSensei on 2012-07-06
In /etc/fstab you should have a line that reads

```
UUID=something none swap sw  0 0 
```

If that's not there you can add it by replacing "something" with the partition's UUID that you'll see using "sudo blkid" as plucky suggests.  On my machine that returns

```
/dev/sda3: UUID="58e6b339-eac1-4acd-a9f2-d640f9b8b8bf" TYPE="swap" 
```

If you use the UUID method in fstab, don't include the quotation marks, just the UUID itself.  The corresponding entry in my /etc/fstab is

```
UUID=58e6b339-eac1-4acd-a9f2-d640f9b8b8bf none  swap    sw   0  0
```

You'll need to be root to edit /etc/fstab.  Use "sudo nano /etc/fstab" or some other editor instead of nano like vi.

---

### Post by jroa on 2012-07-06
Never mind, I am dumb.  I thought that since I set swapon in GParted from a live USB, that it will carry over to installed Ubuntu, but apparently it does not work that way.  I used GParted on the installed Ubuntu and set swapon and now my swap space is recognized. 

At least I learned something new today.

Thanks anyway for your help.  Will set this to solved now.

---

### Post by oldfred on 2012-07-06
If swap is mounted as above, it is normal not to see swap used especially if you have lots of RAM.

Swap is at least 10 time slower than RAM, so you really do not want to use it if you can avoid it. 

Also Ubuntu may show lots of RAM  in use, but that is because it also uses RAM as cache since the same task is often reused. It only frees that if needed for new tasks and then only if all new/working tasks fill RAM is swap used. With 4GB of RAM I almost never use swap. But I understand video editing can use as much RAM as you can throw at it.

---

### Post by jroa on 2012-07-06
I don't think I ever really remember seeing much swap used on my computer.  Just out of curiosity, I checked it today and saw that 0 was available, and I got a little concerned.  But, it is fixed now.

In fact, I currently have Chrome, AutoCAD, XP VM running netflix, terminal, and Starcraft: Brood War open all at once and am still not using swap.  Although, only 206 MB of physical memory are free.

---

### Post by plucky on 2012-07-06
> I used GParted on the installed Ubuntu and set swapon and now my swap space is recognized.



Did you update /etc/fstab?

If you don't,then the swap partition will not be mounted on the next reboot.

---

