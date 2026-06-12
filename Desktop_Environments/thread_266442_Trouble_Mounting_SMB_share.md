---
title: "Trouble Mounting SMB share"
date: 2006-09-27
forum: Desktop Environments
---

### Post by simplenomad on 2006-09-27
I am new to Ubuntu (6.06) and I am trying to mount a network share on my work network (windows based). 
I have followed the instructions in ubuntu guide and have created the .smbcredentials file with my details and I have created a directory i.e. /media/servershare

I have added the following to /etc/fstab
//192.168.8.40/Server    /media/servershare smbfs  credentials=/root/.smbcredentials,dmask=777,fmask=777  0    0

When I try to remount e.g. gksudo mount -a
I get the following:
/dev/sda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
/sys on /sys type sysfs (rw)
varrun on /var/run type tmpfs (rw)
varlock on /var/lock type tmpfs (rw)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
devshm on /dev/shm type tmpfs (rw)
lrm on /lib/modules/2.6.15-23-386/volatile type tmpfs (rw)
/dev/sda1 on /media/windows type ntfs (rw,nls=utf8,umask=0222)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

My SMB mount does not work and I haven't got a clue what this error messages means?
Any help is appreciated.
Thanks,
paul

---

### Post by bernied on 2006-09-27
It's possible that all you need is the auto option with those other options, so:
```
//192.168.8.40/Server /media/servershare smbfs credentials=/root/.smbcredentials,dmask=777,fmask=777**,auto** 0 0
```I believe only entries listed as auto are mounted using the '-a' option (I think the 'defaults' option includes auto, so that would also do, but probably not in this case).

That 'error message' looks like a just a list of mounts, this is not the normal output from 'mount -a', but it could be the normal output from 'mount'. Perhaps you should be using 'sudo' rather than 'gksudo'. gksudo is for gnome x-window applications, sudo is for terminal applications, maybe gksudo is not passing on the '-a' option.

Also try just:
```
sudo mount /media/servershare
```

---

### Post by nathanbriggs on 2006-09-27
I use smb4k which has an easy gui for samba mounts ( I know the command line is king but gui's are SO much easier)

just remember to install super package as well (sudo doesn't play well with smb4k)

sudo apt-get install smb4k super

---

### Post by simplenomad on 2006-09-28
Thanks folks,
The auto option is the one I needed.
I have also download smb4k which I will try out now.
Once again - thanks for your help,
paul

---

