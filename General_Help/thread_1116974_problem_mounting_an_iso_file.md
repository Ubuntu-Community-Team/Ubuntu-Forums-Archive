---
title: "problem mounting an iso file"
date: 2009-04-05
forum: General Help
---

### Post by shangrily on 2009-04-05
I have an iso image and im trying to open it using the program iso master but when i try to open it i get "Failed to read volume info: 'First volume descriptor type not primary like ISO9660 requires'"
i tried using terminal to mount it with no luck and the same with glISOMount and Gmount-iso
is the something wrong with the iso image that im using (do i need to convert it to somthing else?)
im pretty sure it should work because i downloaded it on my other pc and it worked fine.

---

### Post by kestrel1 on 2009-04-05
Sounds like it could be corrupted. If you transfered it from one machine to another how did you do this? USB drive,CD etc.

---

### Post by ajgreeny on 2009-04-05
Try mounting in terminal.  You may get helpful error messages.
```
sudo mount -o loop -t iso9660 path/to/file.iso /mount/path
```

---

### Post by shangrily on 2009-04-05
i downloaded it via torrent from the same place i got it last time

---

### Post by shangrily on 2009-04-05
> **ajgreeny said:**
> Try mounting in terminal.  You may get helpful error messages.
```
sudo mount -o loop -t iso9660 path/to/file.iso /mount/path
```

here is the message i get when i use that

/home/flyboy/desktop/rld-fou3.iso: No such file or directory

here is how i put it in 

sudo mount -o loop -t iso9660 /home/flyboy/desktop/rld-fou3.iso /mnt

---

### Post by shangrily on 2009-04-05
im going to try using transmission's verify local data option ill let you know how it goes

---

### Post by ajgreeny on 2009-04-05
> **shangrily said:**
> here is the message i get when i use that

/home/flyboy/desktop/rld-fou3.iso: No such file or directory

here is how i put it in 

sudo mount -o loop -t iso9660 /home/flyboy/desktop/rld-fou3.iso /mnt
I think it should probably be /home/flyboy/Desktop in the command, not desktop.  Don't forget linux is case sensitive, so check the rest of the command as well.  You may also need to make a separate folder in /mnt to mount to, eg ```
sudo mkdir /mnt/isomount
```

---

### Post by shangrily on 2009-04-05
i think it was that the file was missing some stuff
so i an extracting it from the archive again
ill try changing the case when its done thank you
ill post later if it dose not work

---

### Post by shangrily on 2009-04-05
did not work got this result

mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
tried dmsg and had this as the error 

ISOFS: Unable to identify CD-ROM format.

i think that means its not a iso9660 is there any way to tell?

---

### Post by shangrily on 2009-04-05
problem solved
used this format

sudo mount -o loop /path/to/file.iso /mountpoint

---

### Post by Slim Odds on 2009-04-05
> **ajgreeny said:**
> Try mounting in terminal.  You may get helpful error messages.
```
sudo mount -o loop -t iso9660 path/to/file.iso /mount/path
```

What is it's a UDF disk and not ISO9660?

---

### Post by archeryguru2000 on 2009-07-14
> **shangrily said:**
> problem solved
used this format

sudo mount -o loop /path/to/file.iso /mountpoint

Hey shangrily, I've been having the same problems with a game image.  I assumed I was just having problems with the size (>6GB).  However, omitting the "-t iso9660" option finally allowed the image to be mounted.  I'm glad you posted how you were able to finally mount yours.  This helped me as well!

Thanks,
~~archery~~

PS  I wonder if there is a way to add this option (or actually omit this option) in Gmount-iso.  This is my preferred choice for mounting image files.

---

