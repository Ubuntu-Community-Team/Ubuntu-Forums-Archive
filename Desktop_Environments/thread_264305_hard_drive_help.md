---
title: "hard drive help"
date: 2006-09-24
forum: Desktop Environments
---

### Post by Magiczero on 2006-09-24
Hi 

I have a hard drive that is internal and I cant get it to work...  I have tries many things.  I have formated it in all of the formating ways even as a windows drive.  That doesnt work!  
I get this error:  mount: only root can mount /dev/hdb1 on /foo
I have gone into the /etc/fstab file and this is what I get
> # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda1 / ext3 defaults,errors=remount-ro 0 1
/dev/hda5 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0

When I put the drive in a windows box it works but, not in ubuntu

I have done everything I can think of to do!

I did the mount command and that wont work either so I'm lost here!
Note:  This is a 2nd drive...  It is not my main boot drive
Any Help here would be great!

Thanks a lot!

---

### Post by Ramses de Norre on 2006-09-24
Have you tried to put "sudo" in front of the mount command? This makes you execute the command with root priviliges.
You'll see a password prompt and you have to enter your own userpassword (and it's normal you don't see any characters, just keep on typing the password).

More [info](http://wiki.ubuntu.com/RootSudo).

Also make sure your mountpoint exist and you give the right options to your command, post back the command if it still doesn't work.

---

### Post by Magiczero on 2006-09-24
yes I trid all that to and it still isnt working

---

### Post by Ramses de Norre on 2006-09-24
What's the error then?? What's the command you use??
You need to give us some more info.

---

### Post by Magiczero on 2006-09-24
I type > Sudo mount
When I type that I get
> tanner@tanner-desktop:~$ sudo mount
Password:
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
tanner@tanner-desktop:~$






Then when I go to Places<Computer and click on the drive I get this error
> Unable to mount the selcted volue
mount: only root can mount /dev/hdb1 on /foo



---

### Post by Ramses de Norre on 2006-09-24
Ok, now I know what's wrong. You need to give parameters to the mount command to mount a drive.

But a better way is adding the drive in /etc/fstab, if you tell me the file system and were you want to mount it I'll give you a proper fstab line.

---

### Post by Magiczero on 2006-09-24
Ok great!!  So what you need me to give you?

---

### Post by Ramses de Norre on 2006-09-25
```
sudo mkdir /media/hdb1
sudo gedit /etc/fstab
```
And add this line:
```
/dev/hdb1       /media/hdb1     ext3    nodev,nosuid        0       2
```
```
sudo mount -a
```
Your files are accessible in /media/hdb1.

---

