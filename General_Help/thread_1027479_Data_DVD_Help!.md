---
title: "Data DVD Help!"
date: 2009-01-01
forum: General Help
---

### Post by edp123 on 2009-01-01
When I insert a Data DVD into the computer, Ubuntu 8.10 tells me..
 
Unable to mount the volume 'MY_MP3_122908'.

In the details, it says..

[mntent]: line 9 in /etc/fstab is bad
[mount]: can't find /media/cdrom0 in /etc/fstab or /etc/mtab

can anybody help?

---

### Post by taurus on 2009-01-01
Create the new mount point.

Applications -> Accessories -> Terminal
```
sudo mkdir /media/cdrom0
```
Then, insert the DVD in again.

Or post your /etc/fstab.

```
cat /etc/fstab
```

---

### Post by edp123 on 2009-01-01
Here's the /etc/fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=1c907250-bdd9-4903-9d45-5f13da6c76fd /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=87e9813c-3b6e-4486-99be-7f1a3435df97 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0# # 1002 is the USB group
none /proc/bus/usb usbfs devgid=1002,devmode=666 0 0

---

### Post by taurus on 2009-01-01
Create the mount point, /media/cdrom0, if you don't already have it.

```
sudo mkdir /media/cdrom0
ls -la /media
```

---

### Post by edp123 on 2009-01-01
I did that and this is what happened...

lalo@lalo-desktop:~$ sudo mkdir /media/cdrom0
[sudo] password for lalo: 
mkdir: cannot create directory `/media/cdrom0': File exists
lalo@lalo-desktop:~$ ls -la /media
total 12
drwxr-xr-x  3 root root 4096 2009-01-01 10:13 .
drwxr-xr-x 20 root root 4096 2008-12-23 22:47 ..
lrwxrwxrwx  1 root root    6 2008-12-23 22:14 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2008-12-23 22:14 cdrom0
-rw-r--r--  1 root root    0 2009-01-01 10:13 .hal-mtab


it still wasn't able to mount when I re-inserted the data DVD.

---

### Post by prshah on 2009-01-01
> **edp123 said:**
> When I insert a Data DVD into the computer, Ubuntu 8.10 tells me..

[mntent]: line 9 in /etc/fstab is bad
[mount]: can't find /media/cdrom0 in /etc/fstab or /etc/mtab


From 8.10 onwards, cdrom and other removable devices are handled by HAL (dynamic) and hence require no entry in the fstab. So I'm guessing that you've upgraded, and then manually entered the lines for the CDROM in the /etc/fstab.

In any case, right guess or not, you can comment out any lines relating to fd and scd/cdrom/dvd devices in the /etc/fstab, then reboot and check; do the devices work properly now?

---

### Post by edp123 on 2009-01-01
How do I 'comment out' these line you speak of?
Sorry if it's a dumb question, but I'm rather new to Linux and Ubuntu.

---

### Post by prshah on 2009-01-01
> **edp123 said:**
> How do I 'comment out' these line you speak of?
Sorry if it's a dumb question, but I'm rather new to Linux and Ubuntu.

Place a "#" (hash) character (no quotes) in front of the line (as the first character).

To edit the file, press Alt+F2, and give the command ```
gksudo gedit /etc/fstab
``` The screen will go black(ish) and you will be asked for your password, since this is a system critical file that you want to edit.

Edit, save, quit and restart to check if the DVD drive works.

---

### Post by edp123 on 2009-01-01
Wow, thanks a lot man.
This Ubuntu OS is really complicated and what not, but im really trying to give it a chance! 
Thanks again. :D

---

