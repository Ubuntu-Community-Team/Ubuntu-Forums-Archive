---
title: "Can't access partitions in Thunar."
date: 2009-02-11
forum: General Help
---

### Post by Query on 2009-02-11
I just installed Xubuntu 8.10 for the first time in my life and I'm trying to adjust myself in it. I have dual boot with Windows XP in C and Xubuntu in D. I'm experiencing quite a few problems but right now this is the most irritating one:

I can't access my C or D drive in Xubuntu. When I open the File system icon on the desktop it takes me all the boot, bin, cdroom, dev, home etc folders. I don't know how to access the C or D the way I used to in Windows. In windows the files systems of C and D are FAT-32. If I open Firefox>>>>Open File, I get both the C and D under different names i.e C is called "19.9 GB Media" and D is called "LOCAL DISK" and if a drag a file from there into VLC player or any other program it runs flawlessly. How do I get to my C and D partitions normally?

The File Manager is Thunar. I installed Nautilus and everything works fine in it but I want to use Thunar because its very light weight. 

Thanks in advance

---

### Post by Elfy on 2009-02-11
What do you mean normally? You can get it so they are both mounted at startup and will be available where you decide to put them.

The 19.9Gb Media and Local Disk is farily normal - if you want help to get them mounted at startup please open a terminal and run this command - it will ask for a password - it is your normal one - it will also not show when you type.

```
sudo fdisk -l
```that is a lower case L not a 1

Also - what do you want to call your disks?

---

### Post by Query on 2009-02-11
> **forestpixie said:**
> What do you mean normally? You can get it so they are both mounted at startup and will be available where you decide to put them.

The 19.9Gb Media and Local Disk is farily normal - if you want help to get them mounted at startup please open a terminal and run this command - it will ask for a password - it is your normal one - it will also not show when you type.

```
sudo fdisk -l
```that is a lower case L not a 1

Also - what do you want to call your disks?

Thanks for the answer mate. I did what you said, it asked for the password and then displayed a a list of all drives on my PC. I want the drives to appear in the left panel of the file manager and on the desktop. Naturally I would like it if they are called C and D but thats not a big issue.

---

### Post by Elfy on 2009-02-11
Heh - yes I know what it does - kinda expecting you to post it so I could see - but for the moment I will assume that they are called sda1 and sda2 - if they're not you will need to bear in mind the difference 

If you run this from a terminal it will give you the UUID for oyur drives - you need the number that is given for sda1 and sda2 

```
blkid
```

You will need the numbers given for each to enter below directly after UUID= followed by a space

UUID=[COLOR="Red"]numberfromblkid[/COLOR] 

Now make 2 folders to mount the drives in

```
sudo mkdir /media/C /media/D
```

Now we want to backup and edit a file called fstab

```
sudo cp /etc/fstab /etc/fstab.bak
gksudo mousepad /etc/fstab
```


Add this to the bottom of the file - best to copy and paste

```

##Windows Drives
UUID= /media/C vfat auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=1 37 0 0

UUID= /media/D vfat auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=1 37 0 0

```

On reboot they should be mounted on your desktop as C and D

---

### Post by Query on 2009-02-12
> **forestpixie said:**
> Heh - yes I know what it does - kinda expecting you to post it so I could see - but for the moment I will assume that they are called sda1 and sda2 - if they're not you will need to bear in mind the difference 

If you run this from a terminal it will give you the UUID for oyur drives - you need the number that is given for sda1 and sda2 

```
blkid
```

You will need the numbers given for each to enter below directly after UUID= followed by a space

UUID=[COLOR="Red"]numberfromblkid[/COLOR] 

Now make 2 folders to mount the drives in

```
sudo mkdir /media/C /media/D
```

Now we want to backup and edit a file called fstab

```
sudo cp /etc/fstab /etc/fstab.bak
gksudo mousepad /etc/fstab
```


Add this to the bottom of the file - best to copy and paste

```

##Windows Drives
UUID= /media/C vfat auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=1 37 0 0

UUID= /media/D vfat auto,users,uid=1000,gid=100,utf8,dmask=027,fmask=1 37 0 0

```

On reboot they should be mounted on your desktop as C and D

OK. I did exactly what you said but nothing has shown up on desktop. Although, C and D folders have appeared in the media folder of the File system.

---

