---
title: "media questions"
date: 2005-08-12
forum: Desktop Environments
---

### Post by uperjer on 2005-08-12
something that will really help ween me off windows xp would be the ability to 

a) access music and video files from my ntfs and fat32 formatted hard drives

b) ability to play .mp3 and .wma files 

c) a good media player with similar organisational features as itunes

d) ability to play dvds

any feedback and/or help would be greatly appreciated. i'm really enjoying kubuntu thus far, and would really like to make it my primary operating system instead of xp.

---

### Post by amohanty on 2005-08-12
> a) access music and video files from my ntfs and fat32 formatted hard drives 

mkdir
mount -t ntfs /dev/<ntfs-drive spec> /mnt/ntfs1

> ability to play .mp3 and .wma files, DVD  
what i use:
totem-xine win32codecs beep-media-player


> a good media player with similar organisational features as itunes 
_A_... look around you will find a 100...

HTH
AM

---

### Post by f1dave on 2005-08-12
A good music player? Amarok.

Wanting to access your mp3s? 
The mount command each time can get a bit annoying, you may want to look at adding a line to your /etc/fstab like I have below:

```
/dev/sda1       /media/windows  auto    ro,user,umask=666   0       0
/dev/hda5       /media/fat1     vfat    rw,user         0       0
/dev/hdb5       /media/fat2     vfat    rw,user         0       0
```

The top line is to enable read only access to my ntfs partition on my 80G SATA drive, which it shares with my linux partition. The next two make my FAT32 drives accessible for linux for read and write.

Hope that helps you

---

### Post by BKK on 2005-08-13
[QUOTE=f1dave]A good music player? Amarok.

Wanting to access your mp3s? 
The mount command each time can get a bit annoying, you may want to look at adding a line to your /etc/fstab like I have below:

```
/dev/sda1       /media/windows  auto    ro,user,umask=666   0       0
/dev/hda5       /media/fat1     vfat    rw,user         0       0
/dev/hdb5       /media/fat2     vfat    rw,user         0       0
```

The top line is to enable read only access to my ntfs partition on my 80G SATA drive, which it shares with my linux partition. The next two make my FAT32 drives accessible for linux for read and write.

Hope that helps you[/QUOTE]

Thanks I tried both options.

The mount command:
tried to mount in Konsole. Kubuntu said only root can do that. Then I logged in through console mode as root and kubuntu said mount point ntfs1 does not exists. Anyways I dont understand all the commands. If I have to log on then off again to get root access this is pointless ..right?

next trying to add that code:

Using kate to add the lines of code Kubuntu again says that I do not have permisson!!
It wouldnt let me log on as root either ( into KDE I can get into the text only thing, but again i am newb so the commands are a foreign language still)

What am I doing wrong here??

---

### Post by z-vet on 2005-08-13
[quote="BKK"]kubuntu said mount point ntfs1 does not exists[/quote]
Yes, you need to create it... 
```
sudo mkdir /media/ntfs1
```
You need to run Kate as root to get a write permission for /etc/fstab. Or, if you have MC installed, run it in Konsole as root:
```
sudo mc
```
Then browse to /etc, find fstab and press F4 to edit it.

---

