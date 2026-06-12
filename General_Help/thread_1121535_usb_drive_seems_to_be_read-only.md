---
title: "usb drive seems to be read-only"
date: 2009-04-10
forum: General Help
---

### Post by elymic on 2009-04-10
Hi, I'd like ask about a problem related to my usb drive (Maxtor 500gb), for some reason xubuntu doesn't allow me to copy anything into it and tells me "Read-only file system" on my attempts to create folders and change files. How can I solve this?
thanks

---

### Post by _Purple_ on 2009-04-10
Did you check the permission if its set to root only? 
If not, you can try backing up the files and then format the usb drive using gparted.

---

### Post by coffeecat on 2009-04-10
What is the filesystem on the USB drive? If you're not sure, plug it in, open a terminal and post the output of:

```
sudo fdisk -l
```Also, please confirm the release number of Xubuntu you are using. Your profile says: "Ubuntu 7.10 Gutsy Gibbon", which is a now unsupported release, and which is not Xubuntu.

If that Maxtor drive is formatted NTFS and you are using an obsolete release, that might be the problem. NTFS write support is fairly recent. It was in 8.04 Hardy but I can't remember whether it was in Gutsy. Anyway, sudo fdisk -l will tell us what we need to know.

---

### Post by elymic on 2009-04-11
Thanks for the replies! my usb exxternal drive is NTFS, and I have xubuntu 8.10 installed. The problem is that I have difficulties with accessing my data partition on my inner drive, and I need the external "writable" usb drive to copy my data to it, then formatting the damaged partition. But now I reached a dead-end because I can't use my usb drive to backup the data, and there's not enough space on the inner drive to backup the usb before formatting.
now this is frustrating!
is there a way to allow for writing files and folders to the usb without fdisk?

---

### Post by _Purple_ on 2009-04-11
> **elymic said:**
> Thanks for the replies! my usb exxternal drive is NTFS, and I have xubuntu 8.10 installed. The problem is that I have difficulties with accessing my data partition on my inner drive, and I need the external "writable" usb drive to copy my data to it, then formatting the damaged partition. But now I reached a dead-end because I can't use my usb drive to backup the data, and there's not enough space on the inner drive to backup the usb before formatting.
now this is frustrating!
is there a way to allow for writing files and folders to the usb without fdisk?

Can you please post the outputs of the following command once before plugging in your USB drive and once after plugging it in?

Open terminal and type:

```
ls -l /media
```

---

### Post by elymic on 2009-04-12
this is the list before connecting the usb drive:

total 8
lrwxrwxrwx 1 root root    6 2009-04-04 22:18 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2009-04-04 22:18 cdrom0
drwxr-xr-x 2 root root 4096 2009-04-10 12:07 harddrive


this is after:

total 12
lrwxrwxrwx 1 root root    6 2009-04-04 22:18 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2009-04-04 22:18 cdrom0
drwxr-xr-x 2 root root 4096 2009-04-10 12:07 harddrive
drwxrwxrwx 1 root root 4096 2009-02-20 11:38 OneTouch 4

---

### Post by _Purple_ on 2009-04-13
Change the permission of the USB drive which is OneTouch 4. It shows that access is given to root only.

---

### Post by elymic on 2009-04-14
Thanks Purple, but the chmod doesn't work for me. Like you wrote, the usb drive is called "OneTouch 4", and the command can't access this directory because of the space before the "4". Needless to say I can't rename that drive because I don't have the permission to do it, and sudo mv can't deal with this name either.

---

### Post by _Purple_ on 2009-04-14
Try using
```
"OneTouch 4"
```

Or

```
OneTouch\4
```

---

### Post by elymic on 2009-04-14
Thank you for replying so fast! just to confirm, should I type :

sudo chmod 777 /[path]/

to have write and read permission?

tnanks again

---

### Post by sedawk on 2009-04-14
> **elymic said:**
> this is the list before connecting the usb drive:

drwxrwxrwx 1 root root 4096 2009-02-20 11:38 OneTouch 4

The directory is world-writable, so access rights seem to be fine.

First you can check if root is allowed to create a file:
```

sudo touch "/media/OneTouch 4/root_touch.txt"

```
If you get an error the file system is mounted read only, this
can happen if NTFS is "unclean". 
Before connecting the drive run "sudo dmesg -c" to clear message buffer
and after connecting the drive run "dmesg" to view message buffer.
There should be some interesting output after connecting the drive.
In the past you had to connect the drive to a Win-PC, but 
I think you can fix this my mounting the drive manually using
the "force" option for NTFS. Continue with reading "man mount.ntfs"
document or search the web for examples.

---

### Post by _Purple_ on 2009-04-14
> **elymic said:**
> Thank you for replying so fast! just to confirm, should I type :

sudo chmod 777 /[path]/

to have write and read permission?

tnanks again

Yes.
```
sudo chmod 777 /media/OneTouch 4
```

You can do it using GUI too. Open terminal and type:
```
gksudo nautilus
```
This will open the GUI with root permission. You can go to the media folder and right-click on OneTouch 4 and go to properties. You can set the the read, write permissions.

---

### Post by elymic on 2009-04-14
I'm sorry for writing again but things are not working yet, both chmod and chown don't cause any change, and running gksudo thunar (in my xubuntu) doesn't allow me to change the usb's owner. It does mention read and write permission for all the users, but still blocks me when I try to create a folder. "touch" is blocked either.

---

### Post by _Purple_ on 2009-04-14
Sorry I did not notice that you are using Xubuntu. The GUI will work for nautilus, I am not sure about xfce. Looks like your pronblem is what sedawk has mentioned.

---

