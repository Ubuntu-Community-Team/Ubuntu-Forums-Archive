---
title: "problems"
date: 2009-02-28
forum: General Help
---

### Post by uns3r on 2009-02-28
i downloaded ubuntu 8.10 and it removed vista so now i want to know how to give ubuntu more space cause otherwise i am going to run out of spcae 
would like to know asap

---

### Post by s.fox on 2009-02-28
Try gparted, that should help you do what you want

-hope this helps

---

### Post by sgosnell on 2009-02-28
Are you sure it removed Vista?  It would normally leave the Vista partition untouched, and add a new partition for Ubuntu.  You should be able to boot into either Vista or Ubuntu by pressing Esc at the start of the boot process.  You may be able to resize any of the partitions by using GParted - System, Administration, Partition Editor.

---

### Post by uns3r on 2009-02-28
where can i download Gparted from i dont understand how to get it
and i dont have the partion editor

---

### Post by s.fox on 2009-03-02
> **uns3r said:**
> where can i download Gparted from i dont understand how to get it
and i dont have the partion editor

Hi,

Sorry, I really should have given a link.

1) Download the GParted Live-CD ([http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php))
2) burn it and boot it.

-hope this helps

---

### Post by mjs1512 on 2009-03-02
Thanks for the GParted link it is what I have been looking for to remove the ntfs file system on my back up drive.
Having recently installed 8.1 to replace Vista, I taking the last step to remove every thing MS from my machine. So when I run GParted which format should I choose to replace the NTfs file system. By default it offers msdos?
but that sounds to much like microsoft to be the best option.
I also want to make a folder on this drive available to two other users on my home network. Both these pc's are using XP and I want to backup data/files from them on my pc while I upgrade them both to Ubuntu.
cheers  Marty

---

### Post by uns3r on 2009-03-06
is there a way that i could get vista back
cause i cant run like any game on Ubuntu that i want to 
such as World of Warcraft, which it wont load properly and guild wars which ends up loading upside down
there are other games that I like to play such as Warhammer online and lotro that are not supported either

---

### Post by namegame on 2009-03-06
> **uns3r said:**
> is there a way that i could get vista back
cause i cant run like any game on Ubuntu that i want to 
such as World of Warcraft, which it wont load properly and guild wars which ends up loading upside down
there are other games that I like to play such as Warhammer online and lotro that are not supported either

You'll either need the System Recovery disks that might have come with your Computer, or you will need the Vista install disks. Essentially, assuming that your Vista partition is truly gone, you'll need to reinstall Vista.

---

### Post by uns3r on 2009-03-06
> **namegame said:**
> You'll either need the System Recovery disks that might have come with your Computer, or you will need the Vista install disks. Essentially, assuming that your Vista partition is truly gone, you'll need to reinstall Vista.

my computer came with no discs 
is there a way to get vista back without any discs

---

### Post by namegame on 2009-03-06
> **uns3r said:**
> my computer came with no discs 
is there a way to get vista back without any discs

If your Vista partition has actually been deleted, no.

Perhaps your grub has an issue.

Could you run the following command in a terminal and post the output.

```
sudo fdisk -l
```

This command will list your partitions and their respective types. Maybe your grub just doesn't have a Windows entry.

---

