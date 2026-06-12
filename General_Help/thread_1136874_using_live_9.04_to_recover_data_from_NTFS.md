---
title: "using live 9.04 to recover data from NTFS"
date: 2009-04-25
forum: General Help
---

### Post by itinko on 2009-04-25
I have an HP Vista DV9000 laptop which won't boot. HP has suggested restoring factory image. I'm trying to use 9.04 Desktop Live CD to recover some data (mostly photos)from Vista NTFS partition before restoring the factory Vista image. I can boot Ubuntu and see the NTFS drive but when I drill down into existing folders it shows me no files. I tried to search the drive for *.jpg and nothing showed up. I presume there is some NTFS file security present. Does anyone know a way I can login to access the HD or see those files some other way?

Thanks for any help!

---

### Post by albinootje on 2009-04-25
> **itinko said:**
> I can boot Ubuntu and see the NTFS drive but when I drill down into existing folders it shows me no files.

Try in a terminal :
```

gksu nautilus

```
and then browse via "File system" to the subdirectory in /media/   
where the NTFS partition is mounted.

---

### Post by itinko on 2009-04-25
Thanks for your suggestion. I still can't see any files in the user folders. I'll contact MS Vista Forum to see if there is a way around this.

---

### Post by regor210 on 2009-04-25
From the Live CD go to Places and clkick on the Hard drive you want to access.

in a terminal use 

$gksu nautilus 

Then click on the  <  (Up next to the root icon). Now click on the hard drive icon. Next click on the media icon in the window.  If you only mounted the drive you needed click on the disk icon. Now your where you need to be. 

Note. your in root so make wise choices.

---

### Post by itinko on 2009-04-25
Thanks so much for that suggestion! I'm really getting enamored with Ubuntu! I can see the files, now I need to figure out how to write a DVD while booted off Ubuntu Live CD. Or connect to my other Vista system to copy images to a share... but when I click on Windows Network it says unable to mount location, failed to retrieve share list from server. Guess I'll have to a bunch more reading ;)

---

### Post by albinootje on 2009-04-25
> **itinko said:**
> when I click on Windows Network it says unable to mount location, failed to retrieve share list from server.

The easiest in my opinion is to install the openssh server on the Ubuntu part (Yes, installation of software is possible during a live session).

Let's assume the NTFS partition is mounted via /dev/sda1 :

```

sudo apt-get install ssh
passwd (temporarily give the live session user a password)
sudo mkdir /media/windows
sudo umount /dev/sda1
sudo ntfs-3g /dev/sda1 /media/windows -o uid=1000,umask=000,force 

```

If the NTFS-partition would be /dev/sda2, use that instead of /dev/sda1 in this example.

Check the current mount, whether it's sda1 or sda2 (or something else) with :
```

mount|grep sd|grep fuse

```

After that is done successfully, install WinSCP on the (other) MS-Windows machine : [http://winscp.sf.net/](http://winscp.sf.net/) and use that to secure  
copy your files over.

---

### Post by itinko on 2009-04-25
Wicked! That is so amazing! Thanks for that!

---

