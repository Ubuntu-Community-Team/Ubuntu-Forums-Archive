---
title: "unable to mount cd-rom's"
date: 2009-01-22
forum: General Help
---

### Post by bowens44 on 2009-01-22
I get the following error when inserting a CD-rom in Ubuntu 8.10:

Unable to mount NEW

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

This happens with ecery cd on both cd drives. I haven't been able to find a solution.

---

### Post by dcstar on 2009-01-22
> **bowens44 said:**
> I get the following error when inserting a CD-rom in Ubuntu 8.10:

Unable to mount NEW

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

This happens with ecery cd on both cd drives. I haven't been able to find a solution.

Post the contents of /etc/fstab

---

### Post by bowens44 on 2009-01-22
> **dcstar said:**
> Post the contents of /etc/fstab

Here it is:


:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f967997c-d370-4c4f-899e-66685779bac8 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=eb5e0377-bf4e-e9a5-b838-9b5ca333e9c7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

//192.168.5.3/MP3  /media/mp3s  cifs  credentials=/root/.smbcredentials,noperm,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//192.168.5.3/linux_bkups    /media/backups   cifs noperm,credentials=/root/.smbcredentials,noperm,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//192.168.5.3/data    /media/data        cifs    noperm,credentials=/root/.smbcredentials,noperm,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//192.168.5.3/Photos    /home/Photos        cifs   noperm,credentials=/root/.smbcredentials,noperm,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

/dev/sda1  /media/photos ext2 defaults 1 0
/dev/sda2  /media/videos ext2 defaults 1 0
/dev/sda3  /media/misc ext2 defaults 1 0

/dev/sdc1 /home/storage ext3 defaults 1 0

---

### Post by dcstar on 2009-01-22
> **bowens44 said:**
> Here it is:


:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=f967997c-d370-4c4f-899e-66685779bac8 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=eb5e0377-bf4e-e9a5-b838-9b5ca333e9c7 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

//192.168.5.3/MP3  /media/mp3s  cifs  credentials=/root/.smbcredentials,noperm,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//192.168.5.3/linux_bkups    /media/backups   cifs noperm,credentials=/root/.smbcredentials,noperm,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//192.168.5.3/data    /media/data        cifs    noperm,credentials=/root/.smbcredentials,noperm,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0
//192.168.5.3/Photos    /home/Photos        cifs   noperm,credentials=/root/.smbcredentials,noperm,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

/dev/sda1  /media/photos ext2 defaults 1 0
/dev/sda2  /media/videos ext2 defaults 1 0
/dev/sda3  /media/misc ext2 defaults 1 0

/dev/sdc1 /home/storage ext3 defaults 1 0

That looks ok, if you do have two CD drives then you might consider adding the following:

```
/dev/scd1 /media/cdrom1 udf,iso9660 user,noauto,exec,utf8 0 0
```

---

### Post by mssever on 2009-01-22
Judging from your error message, it's possible that DBus got wedged. Try ```
sudo service dbus restart
```If that doesn't fix it, try rebooting. (Yes, technically rebooting shouldn't be necessary. But sometimes you save a lot of time by rebooting instead of trying to figure out what needs to be restarted.)

---

### Post by bowens44 on 2009-01-24
Thanks for the replies. I tried the suggestions above, including rebooting but the problem presists. Well for the most part anyway. I get the error every time I insert a CD. However , it appears that the CD is actually mounting. I can usually  access the data if I go to places/removable media. Still, it's very anoying to have this error box continuesly pop up.

---

### Post by mc4man on 2009-01-24
Double check this, from terminal
```
gconf-editor
```
Look in apps -> nautilus -> desktop and see if "volumes visible' is enabled


Plus maybe what this shows

```
cat /etc/udev/rules.d/70-persistent-cd.rules
```

And this with media in both drives (preferably data )and mounted
```
sudo lshw -C disk
```

---

### Post by bowens44 on 2009-01-24
> **mc4man said:**
> Double check this, from terminal
[gconf-editor
Look in apps -> nautilus -> desktop and see if "volumes visible' is enabled

It was set to 'volumes visible' not enabaled. I usually keep it this way to avoid desktop clutter.


> **mc4man said:**
> Plus maybe what this shows

```
cat /etc/udev/rules.d/70-persistent-cd.rules
```
 cat /etc/udev/rules.d/70-persistent-cd.rules
# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
#  (pci-0000:00:14.1-scsi-0:0:1:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:14.1-scsi-0:0:1:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:14.1-scsi-0:0:1:0", SYMLINK+="cdrw", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:14.1-scsi-0:0:1:0", SYMLINK+="dvd", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:14.1-scsi-0:0:1:0", SYMLINK+="dvdrw", ENV{GENERATED}="1"
#  (pci-0000:00:14.1-scsi-0:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:14.1-scsi-0:0:0:0", SYMLINK+="cdrom1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:14.1-scsi-0:0:0:0", SYMLINK+="cdrw1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:14.1-scsi-0:0:0:0", SYMLINK+="dvd1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:14.1-scsi-0:0:0:0", SYMLINK+="dvdrw1", ENV{GENERATED}="1"
#  (pci-0000:00:06.0-scsi-1:0:1:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:06.0-scsi-1:0:1:0", SYMLINK+="cdrom2", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:06.0-scsi-1:0:1:0", SYMLINK+="cdrw2", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:06.0-scsi-1:0:1:0", SYMLINK+="dvd2", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:06.0-scsi-1:0:1:0", SYMLINK+="dvdrw2", ENV{GENERATED}="1"
#  (pci-0000:00:06.0-scsi-1:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:06.0-scsi-1:0:0:0", SYMLINK+="cdrom3", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:06.0-scsi-1:0:0:0", SYMLINK+="cdrw3", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:06.0-scsi-1:0:0:0", SYMLINK+="dvd3", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:06.0-scsi-1:0:0:0", SYMLINK+="dvdrw3", ENV{GENERATED}="1"
# Cruzer (pci-0000:00:02.1-usb-0:5:1.0-scsi-0:0:0:1)
ENV{ID_CDROM}=="?*", ENV{ID_SERIAL}=="SanDisk_Cruzer_0876810CF7403C4E-0:1", SYMLINK+="cdrom4", ENV{GENERATED}="1"
# Cruzer (pci-0000:00:02.1-usb-0:5:1.0-scsi-0:0:0:1)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:02.1-usb-0:5:1.0-scsi-0:0:0:1", SYMLINK+="cdrom5", ENV{GENERATED}="1"


> And this with media in both drives (preferably data )and mounted
```
sudo lshw -C disk
```

 sudo lshw -C disk
  *-cdrom:0               
       description: DVD writer
       product: DVD-RW  DVR-115D
       vendor: PIONEER
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom3
       logical name: /dev/cdrw3
       logical name: /dev/dvd3
       logical name: /dev/dvdrw3
       logical name: /dev/scd0
       logical name: /dev/sr0
       logical name: /media/cdrom0
       version: 1.13
       capabilities: removable audio cd-r cd-rw dvd dvd-r
       configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,nosuid,nodev,utf8 state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom3
          logical name: /media/cdrom0
          configuration: mount.fstype=iso9660 mount.options=ro,nosuid,nodev,utf8 state=mounted
  *-cdrom:1
       description: DVD-RAM writer
       product: DVD A  DH20A4P
       vendor: ATAPI
       physical id: 0.1.0
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom2
       logical name: /dev/cdrw2
       logical name: /dev/dvd2
       logical name: /dev/dvdrw2
       logical name: /dev/scd1
       logical name: /dev/sr1
       logical name: /media/cdrom1
       version: 9P59
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom2
          logical name: /media/cdrom1
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted
  *-disk:0
       description: ATA Disk
       product: WDC WD2500KS-00M
       vendor: Western Digital
       physical id: 0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 02.0
       serial: WD-WCANKF175312
       size: 232GiB (250GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0008ec16
  *-disk:1
       description: ATA Disk
       product: WDC WD1600JS-00N
       vendor: Western Digital
       physical id: 1
       bus info: scsi@3:0.0.0
       logical name: /dev/sdb
       version: 10.0
       serial: WD-WCANM6549233
       size: 149GiB (160GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=a209a209
  *-disk
       description: ATA Disk
       product: ST3500320AS
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdc
       version: SD15
       serial: 9QM2D1HS
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0007a204


Also, I have noticed that if I have CDs in the drives when I boot , they both mount with out apparent problems. Also , when I am having these problems I also have issues with my flash drive not mounting.

---

### Post by bowens44 on 2009-01-24
More info. Maybe relevent , maybe not.  I reenabled the 'volumes visible' via gconf-editor. After booting with CDs in the drives both cd icons appear on the desktop. After ejecting on of those volumes and inserting another, I either get the error message or I get nothing at all. Either way, the icon does not appear on the deskto until I go to places and select the cd drive there.

---

### Post by mc4man on 2009-01-24
Your 70-persistent .... is a **mess**.
Do this if you want to get your /dev links to what they should be

```
gksudo gedit /etc/udev/rules.d/70-persistent-cd.rules
```

Delete all the entries and leave the file looking like this

> # This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-cd-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.


Save and reboot, the file will be rewritten to reflect what you currently have as drives.
Run the sudo lshw -C disk and you'll see the changes,

Plus
run gconf-editor again and set as shown in screen (automount enabled, automount_open your choice, autorun_never not enabled

---

### Post by bowens44 on 2009-01-24
I did as you suggested. I get this error when putting a CD in the first drive:

[I]Unable to mount 080406_0840

DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.[/I]

But the drive mounts.

Inserted a CD in the second drive and it mounted as it should.

ejected both CDs. Inserted CD in first drive. I get the error again.
again the second drive works as it should.

I am beginning to think the problem is somehow related to that first drive.

Could this be a hardware problem?

---

### Post by bowens44 on 2009-01-24
I no longer suspect a hardware problem. I removed the drive I suspect, made the other drive the master. The problem still exists. T

This is making me crazy. This used to work. I don't know what has changed.

---

### Post by mc4man on 2009-01-24
some quick searching indicates many people are getting the that dbus error in all sorts of situations. In most cases the media or drive or device does mount but the error message persists. (in 8.10

You may want to look at your logs (dmesg, kern.log , maybe grep them for "CD-ROM" or "UDMA"

If you get it squared or give up maybe ck. your ...rules again ( only because when you switch out drives you may be 1 upping your /dev links. Not an issue for mounting, just for apps that default to /dev/dvd or /dev/cdrom

---

### Post by bowens44 on 2009-01-24
Thanks for the time you spent on this. It's very much appriciated.

---

### Post by arepaking on 2009-02-15
Hello Bowens44,

Were you able to solve this issue? I am having this very same problem. I created a post under System76 forum (Since I have a System76 Darte Ultra 3 laptop). The post is: [http://ubuntuforums.org/showthread.php?t=1070943]("http://ubuntuforums.org/showthread.php?t=1070943")

I also have a Dell desktop and is working fine. Just my laptop has this problem. 

I would appreciate if you could share any useful information.

Thanks in advance,
ArepaKing

---

### Post by bowens44 on 2009-02-18
> **arepaking said:**
> Hello Bowens44,

Were you able to solve this issue? I am having this very same problem. I created a post under System76 forum (Since I have a System76 Darte Ultra 3 laptop). The post is: [http://ubuntuforums.org/showthread.php?t=1070943]("http://ubuntuforums.org/showthread.php?t=1070943")

I also have a Dell desktop and is working fine. Just my laptop has this problem. 

I would appreciate if you could share any useful information.

Thanks in advance,
ArepaKing

No, no solution. A lot of people have this problem with ubuntu 8.10. I finally gave up and went back to 8.04.  I am just amazed that this issue has gone for so long for so many without a solution.

---

### Post by acdc_rulz on 2009-04-16
Hey all,
       I just ran into this problem myself running Ubuntu 8.10 on my HP NC8000 laptop. When I place a CD audio, data CD, or DVD in the drive, the drive light stays on for a very long time and then finally stops (takes about 2 minutes). I then got the DBus error reported earlier for data CD discs ONLY. Somehow the drive finally mounts and I am able to access it but if I put in another disc, I get the following error message in Nautilus:

Unable to mount location
Can't mount file

and I can't access the drive from that point on in Nautilus.

Downgrading to 8.04 is not an option as I have everything else setup and working correctly in 8.10 including some critical graphics issues. I did not find this issue submitted to Launchpad so I went ahead and submitted a bug:
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/362639](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/362639)

I hope someone there can help me (us) figure out what is causing this error and try to get it fixed. Anyone else figure out what could be causing this and any workaround/fix?

J

---

### Post by himanshu damle on 2009-08-23
the whole of sunday was spent on trying to get to the threads solving the issue of 'unable to mount cd-roms'. came across many and did try the solutions offered, but was quite amazed to find none working (like many other users). why has this problem persisted for so long with 8.10. i would be most appreciating if this could be sorted out. most of my video lectures are burnt on CDs and since being new to ubuntu, iam having some difficulty in finding the way out. please help.
himanshu damle

---

### Post by himanshu damle on 2009-08-23
urgent help sought.

---

