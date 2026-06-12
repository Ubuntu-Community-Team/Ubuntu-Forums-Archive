---
title: "Mounting my old Fedora hard drive in external enclosure - only mounts /boot  ??"
date: 2008-12-25
forum: General Help
---

### Post by andybunted on 2008-12-25
Hi everyone (Merry Christmas!)

Having a bit of trouble which, hopefully, has some kind of simple answer.

Recently I finally got completely sick of Fedora 9 (which I'd been running for about 2 months) and installed Ubuntu 8.10.  Rather than wipe the whole disk I pulled it from the machine and replaced it with a 500GB SATA drive to do a fresh install of Ubuntu.  

There were a few things on the old disk which I'm keen to move across to the new system.  I've since popped the old drive into an external USB enclosure.  It mounts automatically, but only /boot.  Obviously, all of the stuff I want is in /home.

Any way of getting it to mount the other partitions?  Or is this something to do with LVM?

Any and all suggestions appreciated.  Thanks.

Andrew.

---

### Post by taurus on 2008-12-25
Can you post the outputs of these commands from a terminal?

```
sudo fdisk -l
cat /etc/fstab
df -h
```

---

### Post by RealPSL on 2008-12-25
Yes it is LVM related as Fedora puts everything in LVM except /boot. You will need to run ```
sudo apt-get install lvm2
```

Reboot your computer (There are other ways to do this but on a desktop it is just easier and faster to reboot).

Locate your volume groups by running ```
sudo vgscan
```

List the logical volumes by default if I remember correctly Fedora will create 2 1 for swap and the other for the OS and your files ```
sudo vgdisplay -v VolumeGroup00
```

Replace VolumeGroup00 with the volume group name from vgscan

Check the file system for errors with ```
sudo fsck /dev/VolumeGroup/LogVol00
```

Replacing LogVol00 with the correct logical volume from the output of vgdisplay -v

Mount the file system by running the following commands ```
mkdir /tmp/fedora
sudo mount /dev/VolumeGroup00/logvol00 /tmp/fedora
```

You should be able to review you Fedora data at this time.

---

