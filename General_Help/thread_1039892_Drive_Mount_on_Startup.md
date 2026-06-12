---
title: "Drive Mount on Startup?"
date: 2009-01-15
forum: General Help
---

### Post by semi_fiction on 2009-01-15
Hi all, running Ubuntu 8.10 x64, wondering how to get my 150GB NTFS partition to mount automatically on startup so I don't have to mount it manually before reading my music collection on my Vista partition.

If it matters, the ntfs partition is from 32 bit Vista.

---

### Post by iaculallad on 2009-01-15
From your Terminal, create your mount point:

```
sudo mkdir /media/NTFS_Drive
```

Then, open your /etc/fstab file for editing:

```
gksudo gedit /etc/fstab
```

and insert the line of text on the last part of the file:

```
/dev/xxx /media/NTFS_Drive     ntfs    defaults,umask=007,gid=46 0       1
```

Replace xxx with your own drive partition. You can view this by using the command below:

```
sudo fdisk -l
```

Save and Close the file. While on the terminal, mount it:

```
sudo mount -a
```

HTH.

---

### Post by semi_fiction on 2009-01-15
Ah, thanks. seems I was doing it correctly on my first attempt, but forgot to make the directory in /media.

I noticed the forums pulled the "thanks" feature, kind of disappointed.

---

### Post by iaculallad on 2009-01-15
> **semi_fiction said:**
> Ah, thanks. seems I was doing it correctly on my first attempt, but forgot to make the directory in /media.

I noticed the forums pulled the "thanks" feature, kind of disappointed.

I've noticed that too, hopefully, they'll be bringing it back :p Go Ubuntu.

---

### Post by sztomi on 2009-01-16
I miss the thanks feature, too. Count one more thanks :).

---

### Post by bigbrovar on 2009-01-16
How can also do this easily by installing ntfs-config  s```
udo apt-get install ntfs-config 

``` makes the whole process very easy and simple

---

