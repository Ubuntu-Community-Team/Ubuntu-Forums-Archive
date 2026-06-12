---
title: "Media changed: please insert the disk labeled 'Debian GNU/Linux"
date: 2014-04-22
forum: Debian
---

### Post by theotaxis on 2014-04-22
I installed Debian 7 using a USB flash drive "burned" from the first DVD ISO of the Debian installation CD/DVD.

I did a very minimal install without Debian desktop environment, Print server and Standard system utilities.

After installation and a reboot, I was presented with a console with the words Debian GNU/Linux 7 hostname tty1. I supplied the login username and password.

After I typed the command *sudo apt-get install xorg*, an error message popped up stating:

```
Media changed: please insert the disk labeled 'Debian GNU/Linux 7.4.0 _Wheezy_ - Official amd64 DVD Binary-1 20140208-13:47' in the drive and press Enter

```
I inserted the same USB flash drive into the same slot and after waiting for a few seconds, I pressed Enter.

The same error message popped up.

I have tried the following steps on the advice of some of my colleagues:

1. remove/delete all the entries in /etc/apt/sources.list and reboot the computer
2. dmesg shows that the USB thumb drive is mounted on /dev/sdb1
3. sudo mount /dev/sdb1 /media/usb0
4. sudo apt-cdrom -m -d /media/usb0 add

After doing the above, the following error message appears:

[HTML]Using CD-ROM mount point /media/cdrom/
Identifying.......{a long string of alphanumeric characters}
Scanning disc for index files...............
Found 0 package indexes, 0 source indexes, 0 translation indexes and 0 signatures
W: Failed to mount '/dev/sr0' to '/media/cdrom/'
E: Unable to locate any package files, perhaps this is not a Debian disc or the wrong architecture[/HTML]

I prefer to install Xorg (60MB) and gnome-core (400MB) from the USB stick. The NGO that I am working with is in a developing country with a very basic internet access infrastructure. Internet access is very patchy and the average download speed is less than 2 Mbps.

N.B. It appears that the above issue happens to Ubuntu users as well, as documented in AskUbuntu. However the solution offered on AskUbuntu is to simply delete the cdrom entry in the sources.list and use the internet to install and/or update additional packages.

---

