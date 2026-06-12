---
title: "Kernel Panic error durring start-up (init has been corrupted)"
date: 2007-08-27
forum: Dell  Ubuntu Support
---

### Post by JDavid5381 on 2007-08-27
Hello, I am in desperate need of help. I was very careless while changing a protocol setting in my configuration files for my ethernet card, and must have accidentally corrupted my /etc/init files, because now at start-up (I know this from watching the shell) the kernel goes into panic mode because scripts in the /etc/init files have been corrupted (the parent of all processes!). It could be something else causing the kernel to go into panic mode, but I'm quite certain its somthing with the init files, because thats where the kernal panics in the boot-up process, and it mentions in the error about init not responding. Is there any hope of me recovering my hard drive data?? Is it even feasible that I could get my Ubuntu Linux OS running again?
I'm writing right now b/c I made a partition and installed Dapper, but the system I want to recover is Feisty.  Any help or suggestions would be well appreciated, I desperately await replies. . .

---

### Post by raijinsetsu on 2007-08-27
Nothing on your Feisty partition should be corrupted, outside possibly the kernel or your boot settings.
You can mount your Feisty partition in Dapper.

Example:
You have an ATA hard disk listed as "/dev/hda"
It has two partitions "/dev/hda1" and "/dev/hda2".
If you check out your "/etc/fstab" file in dapper, you can find out what partition it is using, and assume that the other partition is your Feisty install.

If you're not up on fstab or Linux devices, post your "/etc/fstab" file, and the output from "ls /dev/hd* /dev/sd*". Do this from the working Dapper install.

---

### Post by JDavid5381 on 2007-08-27
Is there a way I could look at or change my boot setting to see if thats the problem? And if its the kernel, is there a way to fix it/patch it up using any hard disk utilities? I'm going to try what you recommended. . . but right now I'm running TestDisk to see what I can find.

---

### Post by JDavid5381 on 2007-08-27
sudo cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


The above is what I got when looking at my fstab files. However, the part of my hard drive I want to access is /dev/hda1. I think its not listed here because on my Disk Manager it says there is no access pathway specified. How do I find the pathway to enter into the field so that I can mount that hard drive? As you can tell I"m still a learning a lot of this. Thank you.

---

### Post by raijinsetsu on 2007-08-27
You would add something similar to this:

```
/dev/hda1 /media/Feisty ext3 defaults 2 2
```

assuming it was an ext3 filesystem.

For this line to work, you'll also have to "sudo mkdir /media/Feisty".

---

### Post by JDavid5381 on 2007-08-27
Sorry, but could you explain that in a little more detail? What should I add that too? Also, is there a way for me to retrieve the data without running into memory problems (I'm running at full capacity here)? could I copy it onto a cdrom individual items at a time?

---

### Post by raijinsetsu on 2007-08-27
You add that line to your "/etc/fstab" file. Do a "sudo gedit /etc/fstab" or "sudo kate /etc/fstab".
You'll be able to access all the files on your Feisty partition.

---

### Post by JDavid5381 on 2007-08-27
Thank you sooo much. There's a patheway to hda1 now on my Disk Manager which is what I needed.  But now how do I get the data I want back from the Feisty/hda1 partition?

---

### Post by raijinsetsu on 2007-08-28
Well, all of your data should be in your old home directory, so you could do something similar to "cp -R /media/Feisty/home/YourUserName/* ~/"
Or you could use Konqueror or Gnautilus(sp??) to browse to your old home directory and copy the files to your Dapper home :)

---

### Post by tgalati4 on 2007-08-28
Do you have Grub installed?

You can boot into an earlier Feisty kernel and get things back to normal.  Then just reinstall the lastest kernel through Synaptic and you should be good to go.  That is why older kernels are kept around.  They do sometimes get borked.

---

