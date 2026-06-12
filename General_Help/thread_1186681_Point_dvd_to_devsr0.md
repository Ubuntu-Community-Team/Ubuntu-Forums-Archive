---
title: "Point dvd:// to /dev/sr0"
date: 2009-06-13
forum: General Help
---

### Post by nymusicman on 2009-06-13
I'm trying to rip a dvd with tablet encoder which uses mencoder to rip dvd for a format compitable with n810. Anyway, mencoder uses the dvd:// command to use your dvd player. However dvd:// points to /dev/dvd and I want it to point to /dev/sr0 (my first dvd player).

---

### Post by blazemore on 2009-06-13
Possibly use binding in fstab?

```
sudo nano /etc/fstab
```
Add the following line:

```
/dev/dvd    /dev/sr0     none     bind    0 0
```
Then do
```
sudo mount -av
```

---

### Post by anystupidname on 2009-06-13
> **nymusicman said:**
> I'm trying to rip a dvd with tablet encoder which uses mencoder to rip dvd for a format compitable with n810. Anyway, mencoder uses the dvd:// command to use your dvd player. However dvd:// points to /dev/dvd and I want it to point to /dev/sr0 (my first dvd player).

Can't you just?

sudo rm /dev/dvd && sudo ln -s /dev/sr0 /dev/dvd

---

### Post by andrew.46 on 2009-06-13
Hi nymusicman,

> **nymusicman said:**
> I'm trying to rip a dvd with tablet encoder which uses mencoder to rip dvd for a format compitable with n810. Anyway, mencoder uses the dvd:// command to use your dvd player. However dvd:// points to /dev/dvd and I want it to point to /dev/sr0 (my first dvd player).

I have not tested the following but it might get around your problem:

```
mencoder -dvd-device /dev/sr0 *etc*
```

All the best,

Andrew

---

### Post by mc4man on 2009-06-13
If you can't configure your app to use -dvd-device /dev/xxx (where xxx matches drive you wish to use , then you can change the dev/dvd link for that drive. 
Then the best (survives a reboot) is to edit etc/udev/rules.d/70-persistent-cd.rules

(if  your issue is that your /dev/scd0 (sr0) drive has a dev link of /dev/dvd1 or possibly higher

Running this will show you what is what

```
sudo lshw -C disk
```

Post this if inclined (use a maximized terminal for readability

```
cat /etc/udev/rules.d/70-persistent-cd.rules
```

---

### Post by nymusicman on 2009-06-13
> **anystupidname said:**
> Can't you just?

sudo rm /dev/dvd && sudo ln -s /dev/sr0 /dev/dvd

yes but I'm too lazy to do that every time I reboot.

---

### Post by nymusicman on 2009-06-13
> **blazemore said:**
> Possibly use binding in fstab?

```
sudo nano /etc/fstab
```
Add the following line:

```
/dev/dvd    /dev/sr0     none     bind    0 0
```
Then do
```
sudo mount -av
```

This might help, thanks I'll give it a shot. In these days of udev I sometimes forget trusty old fstab is there.

---

### Post by nymusicman on 2009-06-13
> **mc4man said:**
> If you can't configure your app to use -dvd-device /dev/xxx (where xxx matches drive you wish to use , then you can change the dev/dvd link for that drive. 
Then the best (survives a reboot) is to edit etc/udev/rules.d/70-persistent-cd.rules

(if  your issue is that your /dev/scd0 (sr0) drive has a dev link of /dev/dvd1 or possibly higher

Running this will show you what is what

```
sudo lshw -C disk
```

Post this if inclined (use a maximized terminal for readability

```
cat /etc/udev/rules.d/70-persistent-cd.rules
```

sudo lshw -C disk

> 
*-cdrom                                                                    
       description: DVD-RAM writer                                           
       product: DVD Writer 1070r                                             
       vendor: HP                                                            
       physical id: 0.0.0                                                    
       bus info: scsi@1:0.0.0                                                
       logical name: /dev/cdrom1                                             
       logical name: /dev/cdrw1                                              
       logical name: /dev/dvd1                                               
       logical name: /dev/dvdrw1                                             
       logical name: /dev/scd0                                               
       logical name: /dev/sr0                                                
       logical name: /media/cdrom0                                           
       version: RH22                                                         
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram            
       configuration: ansiversion=5 mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted status=ready
     *-medium                                                                                                     
          physical id: 0                                                                                          
          logical name: /dev/cdrom1                                                                               
          logical name: /media/cdrom0                                                                             
          configuration: mount.fstype=udf mount.options=ro,nosuid,nodev,utf8 state=mounted                        
  *-disk:0
       description: ATA Disk
       product: ST3120026A
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 8.01
       serial: 4JT0XGCE
       size: 111GiB (120GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=0009876a
  *-disk:1
       description: ATA Disk
       product: SAMSUNG SV4002H
       physical id: 0
       bus info: scsi@2:0.1.0
       logical name: /dev/sdb
       version: QP10
       serial: 0413J1FT406760
       size: 37GiB (40GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=000c8b64
  *-cdrom
       description: DVD reader
       product: CDRW/DVD SM-352B
       vendor: SAMSUNG
       physical id: 1
       bus info: scsi@3:0.1.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/scd1
       logical name: /dev/sr1
       version: T806
       capabilities: removable audio cd-r cd-rw dvd
       configuration: ansiversion=5 status=nodisc
  *-disk
       description: SCSI Disk
       product: Photosmart 330 s
       vendor: HP
       physical id: 0.0.0
       bus info: scsi@4:0.0.0
       logical name: /dev/sdc
       version: 1.00
       capabilities: removable
       configuration: ansiversion=2
     *-medium
          physical id: 0
          logical name: /dev/sdc


cat /etc/udev/rules.d/70-persistent-cd.rules

> 
# This file maintains persistent names for CD/DVD reader and writer devices.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-cd-aliases-generator.rules
# file; however you are also free to add your own entries provided you
# add the ENV{GENERATED}=1 flag to your own rules as well.
# CDRW_DVD_SM-352B (pci-0000:00:0f.1-scsi-1:0:1:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:1:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:1:0", SYMLINK+="cdrw", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:1:0", SYMLINK+="dvd", ENV{GENERATED}="1"
# DVD_Writer_1070r (pci-0000:00:0f.0-scsi-1:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.0-scsi-1:0:0:0", SYMLINK+="cdrom1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.0-scsi-1:0:0:0", SYMLINK+="cdrw1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.0-scsi-1:0:0:0", SYMLINK+="dvd1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.0-scsi-1:0:0:0", SYMLINK+="dvdrw1", ENV{GENERATED}="1"


As far as I can see everything checks out. Did I miss something.

---

### Post by nymusicman on 2009-06-13
> **blazemore said:**
> Possibly use binding in fstab?

```
sudo nano /etc/fstab
```
Add the following line:

```
/dev/dvd    /dev/sr0     none     bind    0 0
```
Then do
```
sudo mount -av
```

For some reason this didn't work. It was mounted and when I unmounted /dev/dvd it unmounted the physical drive as well but no video software could see the dvd through the symlink. Weird.

---

### Post by mc4man on 2009-06-13
> As far as I can see everything checks out. Did I miss something. 
Your /dev/scd0 drive had a link ot /dev/dvd1 and I assume you'd like /dev/dvd

> description: DVD-RAM writer
product: DVD Writer 1070r
vendor: HP
physical id: 0.0.0
bus info: scsi@1:0.0.0
logical name: /dev/cdrom1
logical name: /dev/cdrw1
logical name: [COLOR="Blue"]/dev/dvd1[/COLOR]
logical name: /dev/dvdrw1
logical name: [COLOR="Blue"]/dev/scd0[/COLOR]
logical name: [COLOR="Blue"]/dev/sr0 [/COLOR]

Very easy to change, it must be changed in the rules file or will revert to present links upon rebooting.

Do you want it to be /dev/cdrom also? (the default device for many music players

---

### Post by mc4man on 2009-06-13
Edit your rules file like this (marked changes in blue

> # CDRW_DVD_SM-352B (pci-0000:00:0f.1-scsi-1:0:1:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:1:0", SYMLINK+="cdrom", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:1:0", SYMLINK+="cdrw", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.1-scsi-1:0:1:0", SYMLINK+="[COLOR="Blue"]dvd1[/COLOR]", ENV{GENERATED}="1"
# DVD_Writer_1070r (pci-0000:00:0f.0-scsi-1:0:0:0)
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.0-scsi-1:0:0:0", SYMLINK+="cdrom1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.0-scsi-1:0:0:0", SYMLINK+="cdrw1", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.0-scsi-1:0:0:0", SYMLINK+="[COLOR="Blue"]dvd[/COLOR]", ENV{GENERATED}="1"
ENV{ID_CDROM}=="?*", ENV{ID_PATH}=="pci-0000:00:0f.0-scsi-1:0:0:0", SYMLINK+="[COLOR="Blue"]dvdrw[/COLOR]", ENV{GENERATED}="1"

if you want the dvd writer to be /dev/cdrom than do the same with symlinks  cdrom and cdrw  (remove the 1's from the dvd writer and add to the cd writer

To edit
```
gksudo gedit /etc/udev/rules.d/70-persistent-cd.rules

```

After editing then reboot, note that this is perfectly safe to do, (when replacing a drive it's good to delete the entries and reboot, the file is the re written based on the new hardware

---

