---
title: "Need help mounting second Drive"
date: 2009-02-16
forum: General Help
---

### Post by Kain000 on 2009-02-16
Hey everyone, 

I need help mounting a second Sata drive, it's pluged in and the BIOS sees it.

I think ubuntu sees it as well (it's listed in the places> computer screen as SCSI drive, but when I try to mount it it just displays an error saying 

Unable to mount location.

Also once mounted I just want to back up to it so how do I format it with a ext 3 filesystem?

thanks for all your help.

---

### Post by Gen2ly on 2009-02-16
Try mounting the drive manually and see if it gives you any better details:

```
mkdir /mnt/secondsata
mount -t <typefilesystem> /dev/<nameofdrive># /mnt/secondsata
```

Look at the end of "dmesg" and it should tell you the name of the drive, or sometime "fdisk -l" will too.  "man mount" Got details on filesystem types.  Also, are you sure the drive is good?

---

### Post by Kain000 on 2009-02-17
lets see I've been looking for some hardware tempiture monotring apps, and found one for the gnome pannel, 

one option is to view the hard drive temps, and the main one is listed as being BOTH

/dev/sg2     and /dev/sdb

where as the other drive that I cannot mount is 

/dev/sg1 and /dev/sda

---

### Post by alfrz on 2009-02-17
what happens when you code:
```

$sudo fdisk -l

```

---

### Post by Kain000 on 2009-02-17
> **alfrz said:**
> what happens when you code:
```

$sudo fdisk -l

```


```
sean@sean-desktop:~$ $sudo fdisk -l
Cannot open /dev/sda
Cannot open /dev/sdb
Cannot open /dev/sdc

```

---

### Post by Kain000 on 2009-02-17
> **Dirk.R.Gently said:**
>   Also, are you sure the drive is good?

yeah, used it in my last build and it's coming online for the BIOS

---

### Post by alfrz on 2009-02-17
I guess you've already tried it with gparted, can gparted analize the drives?

---

### Post by Kain000 on 2009-02-17
> **alfrz said:**
> I guess you've already tried it with gparted, can gparted analize the drives?


I haven't and I'm not sure..   I've only attepted to use Gparted once before to create an image of my disk

---

### Post by alfrz on 2009-02-17
How does the drive looks like if you select it from the top menu? does it say "Unallocated"?

to open gparted:
```

$sudo su
#apt-get install gparted
#gparted

```

---

### Post by Kain000 on 2009-02-17
yes it reads /dev/sta to be unallocated 
does that mean I need to format it?

It should still have all my previous ubuntu install on it

not worried about trashing it tho

---

### Post by alfrz on 2009-02-17
Just right click on the unallocated data and format it to any fs you want, I recommend Fat16 if it is a "media" drive because you will have no trouble to open it in windows.
If you are a more experienced user, you can format it to ext2 or ext3 and install a simple windows program that you can download from [http://www.fs-driver.org/download.html]("http://www.fs-driver.org/download.html") and be able to read/write on it in windows.

The advantages of formatting to extX and not to fatX is that you will never have to defrag your media disc.

---

