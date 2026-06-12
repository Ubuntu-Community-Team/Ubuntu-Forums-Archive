---
title: "Having an issue with second hard drive"
date: 2009-01-08
forum: General Help
---

### Post by ACrofford on 2009-01-08
I just installed Ubuntu yesterday and it is the only OS running on this machine.

I setup Samba and am able to share files with my Windows PC.  There is a second 120GB HD in the Ubuntu PC.  Since I was able to share files I thought I would back some stuff up.  First I copied over my MP3s.  Since doing that it always seems to clock when trying to access the MP3 directory.

I decided to delete the MP3 folder but it will not let me since it says some sub folders are not empty, I checked and they are.  How can I delete these folders?  I tried going to the terminal but am not sure how to get to the second hard drive.

Also, why would it clock when trying to access the folders?  It is kind of funny, I though sharing drives between two different OSs would be the hard part.

Your help is appreciated.

Thanks,
AC

---

### Post by blazemore on 2009-01-08
To delete them, do
```
sudo rm -rfv **Foldername**
```
Be carefuul

---

### Post by aloshbennett on 2009-01-08
Open your mp3 folder in nautilus (file browser). You could then get the complete path to the folder by hitting CTRL + L.
Open a terminal, and 
```
cd "give the folder path here" 
```

Once you are there, try these commands and post back the results. We'll be able to help you then :-)
```

ls -ld .
ls -a *

```

The first one prints the details of the current directory (who's the owner etc)
and the second one prints all the files present in the directory, including hidden ones.

---

### Post by ACrofford on 2009-01-08
> **aloshbennett said:**
> Open your mp3 folder in nautilus (file browser). You could then get the complete path to the folder by hitting CTRL + L.
Open a terminal, and 
```
cd "give the folder path here" 
```

Once you are there, try these commands and post back the results. We'll be able to help you then :-)
```

ls -ld .
ls -a *

```

The first one prints the details of the current directory (who's the owner etc)
and the second one prints all the files present in the directory, including hidden ones.

I tried this but get the message "No such file or directory".

THis is the path /media/WD Drive 2/MP3s/Country

It seems the spaces in the drive name are what is causing my problem.  Not sure how to remedy this.

Thanks for all the help everyone.

---

### Post by aloshbennett on 2009-01-08
space can be overcome by putting them in quotes
```
 cd "/media/WD Drive 2/MP3s/Country"

```

---

### Post by ACrofford on 2009-01-08
> **aloshbennett said:**
> space can be overcome by putting them in quotes
```
 cd "/media/WD Drive 2/MP3s/Country"

```

Thanks for the info.  I feel pretty dumb right now.

AC

---

### Post by ACrofford on 2009-01-08
Looks like I have a corrupt filesystem on my second hard drive WD Drive 2.  I know I should use fsck but am not sure of the syntax and don't know what the /dev/name would be.

Thanks

---

### Post by ACrofford on 2009-01-08
This is the error I get:

"The superblock could not be read or does not describe a correct ext2 filesystem.  If the device is valid and it really contains an ext2 filesystem (and not swap or ufs or something else), then the superblock is corrupt,a nd you might try running e2fsck with an alternate superblock: e2fsck -b 8193 <device>.

I tried e2fsck -b 8193 /dev/sdb but get the same error.

---

### Post by aloshbennett on 2009-01-08
I believe you have mounted the second hard disk as a single partition? (Nothing right or wrong about it, just asking because you have the device name as /dev/sdb) The /etc/fstab file gives you details about what device is mounted what partition.

It might be helpful to install gparted (GNome partition editor), and use that for formatting your secondary hard disk.

---

