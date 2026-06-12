---
title: "how do i get it to auto detect usb drives?"
date: 2005-12-09
forum: Desktop Environments
---

### Post by 0okami on 2005-12-09
Ok, i learned how to mount drives... (im still flaky at it because it seems that for me to to re-mount a drive after I unplug from the port, i have to reboot.... ) I just pwoer the drive off after im done. Is that wrong? i have a feeling it is because i remember rt clicking the mounted folder and selecting "unmount drive"...but that option is not there anymore. 
:( 

----------edit-------------
ok i figured out how to unmount... 
sudo umount /dev/sdd/
```

ookami@Navi:~/Desktop$ umount /dev/sdd/
umount: /dev/sdd is not in the fstab (and you are not root)
ookami@Navi:~/Desktop$ clear

ookami@Navi:~/Desktop$ mount -l
/dev/hda1 on / type ext3 (rw,errors=remount-ro) [/]
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-9-386/volatile type tmpfs (rw,mode=0755)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
/dev/sdd on /home/ookami/Desktop/xs-drive type vfat (rw,uid=1000,gid=100)
ookami@Navi:~/Desktop$ sudo umount /dev/sdd/
Password:*********************
ookami@Navi:~/Desktop$ mount -l
/dev/hda1 on / type ext3 (rw,errors=remount-ro) [/]
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-9-386/volatile type tmpfs (rw,mode=0755)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
ookami@Navi:~/Desktop$

```
So no need to worry about explaining me how to unmount... however, what was that about fstab? is that something i shold worry about?
-----------end edit-----------

I still need help finding a way to get ubuntu to detect my usb drives again, on its own, like it used to do when it was a fresh installation . Something changed and my usb drives are not longer auto mounted. Im sure its something i must have messed up. 

I Dont know how to fix that. I want to fix that. 
Could someone please guide me on this? 

Thanks.

---

### Post by Sokraates on 2005-12-09
Usually pmount is responsible for mounting any device, that is not listed in the fstab. So you should probably check, if pmount is running, though I don't know how.

If you have an entry in the fstab, it will override pmount. eventually it's quite useful, if you use a certain device regularly and want it to have a certain mountpoint.

For more infos on the fstab look [here](http://www.humbug.org.au/talks/fstab/fstab.html).

Unfortunately I don't have the slightes idea, what could be wrong with your system. Well, I'm still a newbie in with Linux. ;)

---

### Post by earobinson on 2005-12-09
This seems to be a problem a lot of users are having i searched the fourms for (usb mount reboot) you should read
[http://www.ubuntuforums.org/showthread.php?t=88885&page=2&highlight=usb+mount+reboot](http://www.ubuntuforums.org/showthread.php?t=88885&page=2&highlight=usb+mount+reboot)
[http://www.ubuntuforums.org/showthread.php?t=91082&highlight=usb+mount+reboot](http://www.ubuntuforums.org/showthread.php?t=91082&highlight=usb+mount+reboot)
Let us know how it goes, also if you search and find a better answer let us know

---

### Post by firenurse4 on 2005-12-09
[QUOTE=earobinson]This seems to be a problem a lot of users are having i searched the fourms for (usb mount reboot) you should read
[http://www.ubuntuforums.org/showthread.php?t=88885&page=2&highlight=usb+mount+reboot](http://www.ubuntuforums.org/showthread.php?t=88885&page=2&highlight=usb+mount+reboot)
[http://www.ubuntuforums.org/showthread.php?t=91082&highlight=usb+mount+reboot](http://www.ubuntuforums.org/showthread.php?t=91082&highlight=usb+mount+reboot)
Let us know how it goes, also if you search and find a better answer let us know[/QUOTE]

I had similar problems and it seemed to be in the gnome-volume-manager. For me, II wound up reinstalling that dameon to get it to work again. My solution there is in the following...

[http://ubuntuforums.org/showthread.php?t=100129]("http://ubuntuforums.org/showthread.php?t=100129")

---

