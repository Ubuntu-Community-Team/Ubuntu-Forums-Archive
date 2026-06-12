---
title: "good back up software?"
date: 2009-03-17
forum: General Help
---

### Post by Arminius on 2009-03-17
hi, I'm a linux newb, and I'm used to norton ghost on windows, where u can just back up the entire drive into a file.

all the back ups on linux I've found just want to back up the home directory, so does anyone know of one that is similer to norton ghost?

---

### Post by Therion on 2009-03-17
You want **Remastersys**.

[http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html)

---

### Post by Peasantoid on 2009-03-17
There's something similar to Apple's Time Machine (you can probably find it by Googling "ubuntu time machine") out there, but I didn't like it much. Your mileage may vary.

---

### Post by ddrichardson on 2009-03-17
Clonezilla, dd and partimage all spring to mind. I prefer partimage and an external USB drive personally.

---

### Post by Nano_ext3 on 2009-03-17
You should get familiar with the command "dd"  You will thank me when you get to know it.  A better command with verbose output, which is basically dd as well is "dcfldd"  Syntax is as follows

```
dcfl if=/dev/sda1/ of=/mnt/backup/backup.image 
```

That is the basic syntax, input file, output file location. Sda1 is can be whatever device id you need it to be (sudo fdisk -l for a full listing of your drives), and the ".image" can be any word, I just use .image for simplicity sake.

You can also specify nifty things like block size:

```
dd if=/dev/sda2 of=/mnt/backup.image bs=4096
```

**Also please note, instead of backup.image, it can be a device location such as "/dev/sdb2" which could be an external drive, but make sure this drive is clean or backed up, as you will lose all information on that drive!**

If you make a** dd **of a PARTITION and wish to restore it, do NOT re install or remove the existing ubuntu image, simply boot to Live CD and dd the image back over. Other than that your good.


See this page for more tips:

**[http://www.newlinuxuser.com/howto-use-the-dd-command/](http://www.newlinuxuser.com/howto-use-the-dd-command/)**

Cheers!

-Nano

---

### Post by Arminius on 2009-03-18
thanks Nano_ext3
I'll try all that out, I find the "sudo fdisk -l" command useful, but I have a few hard drives, and I'm not finding it easy to tell them apart, is there a command that will list which disk has been titled "videos" "misscellanious" and so forth.

---

### Post by Nano_ext3 on 2009-03-18
Sorry, unfortunately I do not know of a tool that will tell you as such.  You just have to know which drive has that folder.  If all you use is linux then note the "linux" entry from "sudo fdisk -l"  When you get to that specific directory, type "pwd" to get the full path name.

Hope this helps,

--Nano

---

