---
title: "no write permission on pendrive  after automount"
date: 2011-08-14
forum: Desktop Environments
---

### Post by Benkinooby on 2011-08-14
Hi,

firstly, I am new here.
I hope I placed the Thread correctly and
that my post is in line with the post guidlines.
Secondly, thank you in advance for all the support
I allready got by reading forum entries or by lurking in #ubuntu.

My post structure:
	[INDENT]my problem
	my aim
	possible causes
	i use
	i tried/checked
	i didn't try
	additional info
		[INDENT]cat /etc/fstab
		mount
		ps -A
		ls -al /media/
		dmesg
		groups[/INDENT]
	footnotes[/INDENT]

**##### my problem:**
When plugging in a pen drive it will be automounted,
but only root (who owns it) has write access to it.
Other users only have write access.
(Neither my user, nor an unmodified test user)

**##### my aim:**
I want to be able to write on my pendrive without any additional manual work after
plugging it in (iirc that is default on a standard ubuntu install).

**##### possible causes:**
I once had a time where I wanted everthing to be minimal.
Might be, that I removed something in connection with my problem.
I reinstalled everything that came to my mind and could be connected to that problem w/o success.
I merely removed stuff than editing stuff (never touched /etc/fstab or /etc/udev/rules.d/*)
so I think I am missing some kind of service, that manages my (user?) permissions or so.

**##### i use:**
ubuntu 10.04 (initially a kubuntu but I remove nearly everything Qt/KDE stuff)
fluxbox (but most gnome services are active)

**##### i tried/checked:**
check my automount setting[1] - did not change the behaviour
	[INDENT]media_automount - is checked
	media_automount_open - is checked
	usbmount - is installed[/INDENT]
ntfs-config - did not help (even after reboot)
manual mount[2] - worked, but i don't want to do that everytime I plug in a pendrive
gksudo users-admin (made sure that amongs others the following entries are checked)
	[INDENT]Access external storage devices automatically
	Administer the system
	Mount user-space filesystems (FUSE)[/INDENT]

**##### i didn't try:**
chmod - seems to be only used for ext* fs
edit /etc/fstab - seems not to be supposed for such variable things like pendrives
	[INDENT]- changing file systems for same pendrive
	- different number of pen drives
	- every pendrive needs its own fstab entry
[/INDENT]
udev rules - i was told to write some, but I am reluctant because
[INDENT]	- i never did that before (so I also didn't mess them up)[/INDENT]
**##### additional info:**
```
benedict@box:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=ca37aa47-3db3-4327-ba9c-07fb8664e9aa /               ext3    errors=remount-ro 0       1
# /boot was on /dev/sda2 during installation
UUID=3bf3939a-abdf-4df8-82aa-726c6f0c26f2 /boot           ext3    defaults        0       2
# /home was on /dev/sda6 during installation
UUID=f1ef926e-b7f4-4153-93dc-db23b589dd3e /home           ext3    defaults        0       2
# swap was on /dev/sda4 during installation
UUID=09f3483c-f93f-46ef-8f23-6fb1f52d9e69 none            swap    sw              0       0
```

```
benedict@box:~$ mount
/dev/sda5 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
none on /var/lib/ureadahead/debugfs type debugfs (rw,relatime)
/dev/sda2 on /boot type ext3 (rw)
/dev/sda6 on /home type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/benedict/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=benedict)
/dev/sdb1 on /media/usb0 type vfat (rw,noexec,nodev,sync,noatime,nodiratime)
```

```
benedict@box:~$ ls -al /media/
total 12880
drwxr-xr-x 11 root root     4096 2011-08-14 15:10 .
drwxr-xr-x 23 root root     4096 2011-07-15 15:00 ..
lrwxrwxrwx  1 root root       45 2010-05-18 02:55 .directory -> /etc/kubuntu-default-settings/directory-media
drwxr-xr-x  2 root root     4096 2011-08-14 14:40 external
-rw-r--r--  1 root root        0 2011-08-11 13:05 .hal-mtab
lrwxrwxrwx  1 root root       42 2010-11-06 17:18 .hidden -> /etc/kubuntu-default-settings/hidden-media
-rw-r-----  1 root root 13121536 2011-01-25 13:25 mini_04.iso
lrwxrwxrwx  1 root root        4 2010-08-03 14:38 usb -> usb0
drwxr-xr-x  4 root root     4096 1970-01-01 01:00 usb0
drwxr-xr-x  2 root root     4096 2010-08-03 14:38 usb1
drwxr-xr-x  2 root root     4096 2010-08-03 14:38 usb2
drwxr-xr-x  2 root root     4096 2010-08-03 14:38 usb3
drwxr-xr-x  2 root root     4096 2010-08-03 14:38 usb4
drwxr-xr-x  2 root root     4096 2010-08-03 14:38 usb5
drwxr-xr-x  2 root root     4096 2010-08-03 14:38 usb6
drwxr-xr-x  2 root root     4096 2010-08-03 14:38 usb7
```

```
benedict@box:~$ dmesg
[ 3711.444189] usb 1-5: new high speed USB device using ehci_hcd and address 8
[ 3711.582047] usb 1-5: configuration #1 chosen from 1 choice
[ 3711.583345] scsi7 : SCSI emulation for USB Mass Storage devices
[ 3711.585765] usb-storage: device found at 8
[ 3711.585780] usb-storage: waiting for device to settle before scanning
[ 3716.584702] usb-storage: device scan complete
[ 3716.585993] scsi 7:0:0:0: Direct-Access     Corsair  Flash Voyager    1100 PQ: 0 ANSI: 0 CCS
[ 3716.595738] sd 7:0:0:0: Attached scsi generic sg1 type 0
[ 3716.608186] sd 7:0:0:0: [sdb] 7864320 512-byte logical blocks: (4.02 GB/3.75 GiB)
[ 3716.609171] sd 7:0:0:0: [sdb] Write Protect is off
[ 3716.609179] sd 7:0:0:0: [sdb] Mode Sense: 43 00 00 00
[ 3716.609184] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 3716.613045] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 3716.613064]  sdb: sdb1
[ 3716.670712] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[ 3716.670741] sd 7:0:0:0: [sdb] Attached SCSI removable disk
```

```
benedict@box:~$ ps -A
  PID TTY          TIME CMD
    1 ?        00:00:01 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 migration/0
    4 ?        00:00:00 ksoftirqd/0
    5 ?        00:00:00 watchdog/0
    6 ?        00:00:00 migration/1
    7 ?        00:00:01 ksoftirqd/1
    8 ?        00:00:00 watchdog/1
    9 ?        00:00:01 events/0
   10 ?        00:00:00 events/1
   11 ?        00:00:00 cpuset
   12 ?        00:00:00 khelper
   13 ?        00:00:00 async/mgr
   14 ?        00:00:00 pm
   16 ?        00:00:00 sync_supers
   17 ?        00:00:00 bdi-default
   18 ?        00:00:00 kintegrityd/0
   19 ?        00:00:00 kintegrityd/1
   20 ?        00:00:00 kblockd/0
   21 ?        00:00:00 kblockd/1
   22 ?        00:00:00 kacpid
   23 ?        00:00:00 kacpi_notify
   24 ?        00:00:00 kacpi_hotplug
   25 ?        00:00:00 ata/0
   26 ?        00:00:00 ata/1
   27 ?        00:00:00 ata_aux
   28 ?        00:00:00 ksuspend_usbd
   29 ?        00:00:00 khubd
   30 ?        00:00:00 kseriod
   31 ?        00:00:00 kmmcd
   34 ?        00:00:00 khungtaskd
   35 ?        00:00:00 kswapd0
   36 ?        00:00:00 ksmd
   37 ?        00:00:00 aio/0
   38 ?        00:00:00 aio/1
   39 ?        00:00:00 ecryptfs-kthrea
   40 ?        00:00:00 crypto/0
   41 ?        00:00:00 crypto/1
   55 ?        00:00:00 scsi_eh_0
   56 ?        00:00:00 scsi_eh_1
   59 ?        00:00:00 scsi_eh_2
   60 ?        00:00:00 scsi_eh_3
   63 ?        00:00:00 kstriped
   64 ?        00:00:00 kmpathd/0
   65 ?        00:00:00 kmpathd/1
   66 ?        00:00:00 kmpath_handlerd
   67 ?        00:00:00 ksnapd
   68 ?        00:00:05 kondemand/0
   69 ?        00:00:04 kondemand/1
   70 ?        00:00:00 kconservative/0
   71 ?        00:00:00 kconservative/1
  283 ?        00:00:00 i915
  292 ?        00:00:00 usbhid_resumer
  350 ?        00:00:00 kjournald
  387 ?        00:00:00 flush-8:0
  411 ?        00:00:00 upstart-udev-br
  416 ?        00:00:00 udevd
  693 ?        00:00:00 bluetooth
  712 ?        00:00:00 kpsmoused
  754 ?        00:00:00 hd-audio0
  822 ?        00:00:00 portmap
  880 ?        00:00:00 kjournald
  883 ?        00:00:00 kjournald
  932 ?        00:00:00 rpc.statd
  935 ?        00:00:00 rsyslogd
  937 ?        00:00:03 dbus-daemon
  955 ?        00:00:00 gdm-binary
  963 ?        00:00:00 avahi-daemon
  964 ?        00:00:00 avahi-daemon
  973 ?        00:00:02 NetworkManager
  975 ?        00:00:00 console-kit-dae
 1045 ?        00:00:00 gdm-simple-slav
 1050 ?        00:00:00 wpa_supplicant
 1056 tty7     00:05:19 Xorg
 1097 tty4     00:00:00 getty
 1102 ?        00:00:00 getty
 1117 tty2     00:00:00 getty
 1118 tty3     00:00:00 getty
 1122 ?        00:00:00 acpid
 1127 ?        00:00:00 cron
 1128 ?        00:00:00 atd
 1208 ?        00:00:00 winbindd
 1211 ?        00:00:00 winbindd
 1230 ?        00:00:00 cupsd
 1304 ?        00:00:00 dbus-launch
 1362 tty1     00:00:00 getty
 1371 ?        00:00:00 gdm-session-wor
 1373 ?        00:00:11 upowerd
 1385 ?        00:00:03 polkitd
 1424 ?        00:00:00 gnome-keyring-d
 1442 ?        00:00:13 fluxbox
 1481 ?        00:00:00 ssh-agent
 1484 ?        00:00:00 dbus-launch
 1485 ?        00:00:00 dbus-daemon
 1489 ?        00:00:02 nm-applet
 1490 ?        00:02:35 conky
 1491 ?        00:00:13 /usr/share/kupf
 1493 ?        00:00:00 gnome-keyring-d
 1515 ?        00:00:01 gconfd-2
 1542 ?        00:00:00 gvfsd
 1547 ?        00:00:00 gvfs-fuse-daemo
 1556 ?        00:02:23 pulseaudio
 1558 ?        00:00:00 rtkit-daemon
 1563 ?        00:00:00 gconf-helper
 1587 ?        00:00:00 dhclient
 1596 ?        00:00:54 xchat
 1688 ?        00:00:00 automount
 1898 ?        00:02:57 midori
 1930 ?        00:00:22 nautilus
 1934 ?        00:00:00 gvfs-gdu-volume
 1936 ?        00:00:01 udisks-daemon
 1937 ?        00:00:00 udisks-daemon
 1942 ?        00:00:00 gvfs-gphoto2-vo
 1944 ?        00:00:00 gvfs-afc-volume
 1947 ?        00:00:00 gvfsd-trash
 1950 ?        00:00:00 gvfsd-burn
 2011 ?        00:02:23 thunderbird-bin
 2265 ?        00:00:00 gvfsd-computer
 2416 ?        00:01:31 gedit
 2483 ?        00:03:20 vlc
 2525 ?        00:00:01 urxvt
 2526 pts/1    00:00:00 bash
 2606 ?        00:00:00 system-tools-ba
 2608 ?        00:00:00 SystemToolsBack
 2964 ?        00:00:00 dbus-launch
 2965 ?        00:00:00 dbus-daemon
 3188 ?        00:00:00 udevd
 3211 ?        00:00:00 scsi_eh_7
 3212 ?        00:00:00 usb-storage
 3217 ?        00:00:00 udevd
 3301 ?        00:00:00 flush-8:16
 3327 ?        00:00:00 gvfsd-metadata
 3346 pts/1    00:00:00 ps
```

```
benedict@box:~$ groups
benedict adm dialout cdrom audio dip video plugdev fuse lpadmin netdev admin sambashare
```

**##### footnotes:**
[1] [https://help.ubuntu.com/community/Mount/USB#Automounting](https://help.ubuntu.com/community/Mount/USB#Automounting)
[2] [https://help.ubuntu.com/community/Mount/USB#Manually%20Mounting](https://help.ubuntu.com/community/Mount/USB#Manually%20Mounting)

---

### Post by paultag on 2011-08-14
Hiyya friend,

This might have some useful information:

[http://superuser.com/questions/53978/ubuntu-automatically-mount-external-drives-to-media-label-on-boot-without-a-us](http://superuser.com/questions/53978/ubuntu-automatically-mount-external-drives-to-media-label-on-boot-without-a-us)

Good luck!

---

### Post by drpjkurian on 2011-08-14
Hi
If you have the package usbmount, it will create the confusion of write permission of pendrive.Please remove that package

---

### Post by Benkinooby on 2011-08-14
Haaaaaaaaaaiiiiiiiiillllllll drpjkurian !

That did it!

```
sudo aptitude purge usbmount
```
This will also remove the package pmount

Just to roll up nicely:
The mounting and permission setting can be done in various ways, e.g.
[INDENT]Nautilus (see my inital post for how-to)
usbmount/pmount
fstab
udev rules
chmod (permissions only, no mounting, only works for ext* file systems, not ntfs/vfat)
[/INDENT]In my case, Nautilus and usbmount interfered and messed up everything.
(Guess I installed usbmount when I removed all the Gnome stuff and wanted automount back)
So I either have to use Nautilus (what I do now) **OR** usbmount (which would provide the automounting even w/o Nautilus)

---

### Post by drpjkurian on 2011-08-15
You are most welcome buddy..

---

