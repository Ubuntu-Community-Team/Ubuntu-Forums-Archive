---
title: "Editing grub"
date: 2007-02-04
forum: Desktop Environments
---

### Post by Klarsin on 2007-02-04
I have mulitple distros on one computer each on different partitions. Three of them are ubuntu and kubuntu but they all say Ubuntu. It also appears that there are two Ubuntus on one partition, however they are the same installation and probably a duplicate. How do I edit this so I can distiguish the difference  between all the Ubuntus?

---

### Post by taurus on 2007-02-04
Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```
Use a difference title for each version.

---

### Post by Klarsin on 2007-02-05
> **taurus said:**
> Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```
Use a difference title for each version.

This shows  as a read-only file so I can't edit it even after logged in as root. Also Mepis is on hda2, Kubuntu on hda6 and Ubuntu edgy is on hda5. Where are these others. Below only shows dapper on hda1:

# ## End Default Options ##

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-27-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

I remember trying this some time ago with the same result. Is there a GUI that neatly does this that will not make mistakes and also gets past the security?

---

### Post by taurus on 2007-02-05
What's the output of this command from a terminal?

```
ls -la /boot/grub/menu.lst
```

---

### Post by Klarsin on 2007-02-05
> **taurus said:**
> What's the output of this command from a terminal?

```
ls -la /boot/grub/menu.lst
```

:~$ ls -la /boot/grub/menu.lst
-rw-r--r-- 1 root root 4051 2007-01-13 17:46 /boot/grub/menu.lst

---

### Post by taurus on 2007-02-05
ARe you sure you can't save it with 

```
gksudo gedit /boot/grub/menu.lst
```

What's the output of this command then?

```
mount
```

---

### Post by Klarsin on 2007-02-06
> **taurus said:**
> ARe you sure you can't save it with 

```
gksudo gedit /boot/grub/menu.lst
```

What's the output of this command then?

```
mount
```

1- No It's not saveable. ERROR- Says I'm not root user

2- ~$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-27-386/volatile type tmpfs (rw)
/dev/hda5 on /media/hda5 type ext3 (rw)
/dev/sde1 on /media/MAXTOR type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)

The problem exists that I have never been able to modify any of these type of files because an error msg says that I am not the root user, even when I log in as root. This has always been like this. Maybe I need to resolve this issue first. This is a major problem!

---

### Post by taurus on 2007-02-06
You've created a password for root!  

What's the output of this command from a terminal?

```
id
```

---

### Post by Klarsin on 2007-02-06
> **taurus said:**
> You've created a password for root!  

What's the output of this command from a terminal?

```
id
```

$ id
uid=1000(kim) gid=1000(kim) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),106(lpadmin),110(scanner),112(admin),1000(kim)

I Guess my root password is the same for my user. Thats the way its supposed to be set up isnt it? Or is this a different situation?

---

