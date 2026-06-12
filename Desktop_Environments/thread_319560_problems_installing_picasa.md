---
title: "problems installing picasa"
date: 2006-12-15
forum: Desktop Environments
---

### Post by gilrim on 2006-12-15
I've been trying to install picasa, but when I run the installer, this happens:

```
dust@ubuntu:/tmp$ sudo dpkg -i picasa_2.2.2820-5_i386.deb
(Reading database ... 122671 files and directories currently installed.)
Unpacking picasa (from picasa_2.2.2820-5_i386.deb) ...
dpkg: error processing picasa_2.2.2820-5_i386.deb (--install):
 failed in buffer_write(fd) (9, ret=-1): backend dpkg-deb during `./opt/picasa/wine/drive_c/Program Files/wine_gecko/components/imglib2.dll': No space left on device
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 picasa_2.2.2820-5_i386.deb
```

even df -h is:
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/vgcrypt-root
                      192M  125M   68M  65% /
varrun                125M   80K  125M   1% /var/run
varlock               125M     0  125M   0% /var/lock
procbususb             10M  116K  9.9M   2% /proc/bus/usb
udev                   10M  116K  9.9M   2% /dev
devshm                125M     0  125M   0% /dev/shm
/dev/hda1             513M   42M  471M   9% /boot
/dev/mapper/vgcrypt-home
                       16G   15G  1.8G  90% /home
/dev/mapper/vgcrypt-tmp
                       64M   54M   11M  84% /tmp
/dev/mapper/vgcrypt-usr
                      3.0G  2.3G  799M  74% /usr
/dev/mapper/vgcrypt-var
                      752M  626M  127M  84% /var

```
(I've installed xfce on top of this: [http://ubuntuforums.org/showthread.php?t=293299](http://ubuntuforums.org/showthread.php?t=293299) , thus the mess:rolleyes: )

---

### Post by Fully216 on 2006-12-16
you can always use automatix to install it.  If you don't want to do that for some reason, it might be the particular package you are using.  Try using another (the version available in the repos for example).

---

### Post by gilrim on 2006-12-16
tried installing using the repos too, and that does sortof the same:
```

dust@ubuntu:/tmp$ sudo apt-get install picasa
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  picasa
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/21.7MB of archives.
After unpacking 82.3MB of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  picasa
Install these packages without verification [y/N]? y
(Reading database ... 122671 files and directories currently installed.)
Unpacking picasa (from .../picasa_2.2.2820-5_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/picasa_2.2.2820-5_i386.deb (--unpack):
 failed in buffer_write(fd) (9, ret=-1): backend dpkg-deb during `./opt/picasa/wine/drive_c/Program Files/wine_gecko/components/imgicon.xpt': No space left on device
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/picasa_2.2.2820-5_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```There should be space availible on the partitions, but as I understand it, /opt isn't encrypted?

is there something else that could be done to check a package? use dpkg to check for dependencies? I've got wine 0.9.22 installed, but from what I read about picasa, it should have some googlyfied version in the package?

---

### Post by gilrim on 2006-12-16
fixed it by resizing the /dev/vgcrypt/root volume, seems picasa needs 77mb free on /opt (or / on my config).

for anyone that might have a similar problem later (and have installed a fully encrypted system using the script above), these are the steps:

```
df -h
```, and look for /dev/mapper/vgcrypt-root, and take that number of megs there, add say 100 to it (I find it's always good to have at least a little space to grow on), and execute this:
```

sudo lvextend -L500M /dev/vgcrypt/root
sudo resize_reiserfs /dev/vgcrypt/root

```

the example above extends the root to 500MB

---

