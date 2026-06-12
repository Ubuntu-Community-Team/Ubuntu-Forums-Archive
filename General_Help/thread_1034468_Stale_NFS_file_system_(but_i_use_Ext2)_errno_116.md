---
title: "Stale NFS file system (but i use Ext2) errno 116"
date: 2009-01-08
forum: General Help
---

### Post by Gondee on 2009-01-08
My friend borrowed my Dell mini and while it was booting up he pressed Ctrl Alt Backspace like 20 times. I don't know why, i think he wanted it to restarte to the bios, but anyway. 

The next time i turned on the computer i got a little bios looking box, says that Gnome could not be started. 

So im left in a termanl. Then i tryed start X and i get this,
```

X: cannot stat /tmp/.X11-unix (stale NFS file handle), aborting. giving up
xinit: Stale NFS file handle (errno 116):unable to connect to X server
xini: no such process (errno 3): server error

```
Anyone know a solution, i tryed navagting the the file it mentioned via the termanl, but after getting in the /temp i could not go any further, saying *stale NFS file system*.

Is this beyond fixing?

---

### Post by dcstar on 2009-01-08
> **Gondee said:**
> My friend borrowed my Dell mini and while it was booting up he pressed Ctrl Alt Backspace like 20 times. I don't know why, i think he wanted it to restarte to the bios, but anyway. 

The next time i turned on the computer i got a little bios looking box, says that Gnome could not be started. 

So im left in a termanl. Then i tryed start X and i get this,
```

X: cannot stat /tmp/.X11-unix (stale NFS file handle), aborting. giving up
xinit: Stale NFS file handle (errno 116):unable to connect to X server
xini: no such process (errno 3): server error

```
Anyone know a solution, i tryed navagting the the file it mentioned via the termanl, but after getting in the /temp i could not go any further, saying *stale NFS file system*.

Is this beyond fixing?

You probably have corrupted or locked file(s) somewhere, you can manually clean out the /tmp directory by booting off a Live CD and mounting the hard disk, and then reboot and see what happens.

---

### Post by Gondee on 2009-01-08
Im gona try that, would i have to go in and manualy delete all the /temp files?

And why does it say NFS, i use Ext2

---

### Post by dcstar on 2009-01-08
> **Gondee said:**
> Im gona try that, would i have to go in and manualy delete all the /temp files?

And why does it say NFS, i use Ext2

Irrelevant, it is just a system message.

---

### Post by albinootje on 2009-01-08
> **Gondee said:**
> Im gona try that, would i have to go in and manualy delete all the /temp files?

You can boot in recovery mode, choose "root shell", and do the following :
```

rm -rf /tmp/       (removes /tmp for the moment)
mkdir /tmp         (creates /tmp again)
chmod 1777 /tmp    (set the right permissions)
telinit 2          (boot into the graphics mode)

```

---

### Post by Gondee on 2009-01-08
> **albinootje said:**
> 
```

rm -rf /tmp/       (removes /tmp for the moment)
mkdir /tmp         (creates /tmp again)
chmod 1777 /tmp    (set the right permissions)
telinit 2          (boot into the graphics mode)

```

I tryed that, but when im trying to delete the tmp is gives me this

```

rm: cannot remove `/tmp/.X11-Unix`: Stale NFS file handle

```
It does that for all the files in the folder.

how to "un-stale them"?

---

### Post by albinootje on 2009-01-08
> **Gondee said:**
> I tryed that, but when im trying to delete the tmp is gives me this

```

rm: cannot remove `/tmp/.X11-Unix`: Stale NFS file handle

```
It does that for all the files in the folder.

how to "un-stale them"?

That's very strange.
Did you actually boot in recovery mode, or are you trying from the desktop still ?

Recovery mode :
```

1. Boot-up computer
2. If GRUB menu is hidden, press Esc to enter the GRUB menu
3. Select Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
   [Or the like, this is for Ubuntu 8.10)
4. Press <Enter> to boot
5. Choose "drop to root shell prompt"

```

If it still doesn't work, please do the following :
```

sudo mkdir /forcefsck
sudo reboot

```
After the forced fsck remove the /forcefsck

---

### Post by Gondee on 2009-01-08
I cannot even get to the root termanl now. It forces me to put in my root password. and after i enter it, it says 
bash: no job control in this shell

And i can never actully get to that options menu that i was able to erlier. 
It does say somthing about there being duplicte blocks though.
And forsome reason its only mounting my drive in a read-only way.

I went ahead and tried your method, first and second, and neither were able to complete or even start.

---

### Post by Gondee on 2009-01-08
I  think i'm going to re-install Ubuntu, because i need to get some work done. and this is eating time. 

thanks for the help though, many thanks =)

---

### Post by albinootje on 2009-01-08
> **Gondee said:**
>  It does say somthing about there being duplicte blocks though.
And forsome reason its only mounting my drive in a read-only way.


Please boot from the Ubuntu installation cdrom, and do a manual file system check on all your Ubuntu partitions.

For example, assuming that /dev/sda3 is one of your Ubuntu partitions on your hard disk :
```

sudo fsck -y /dev/sda3

```

---

### Post by albinootje on 2009-01-08
> **Gondee said:**
> I  think i'm going to re-install Ubuntu, because i need to get some work done. and this is eating time. 

thanks for the help though, many thanks =)

Make sure you make proper backups first ;-) 
GL!

---

