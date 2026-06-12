---
title: "udev-based device naming inconsistent after upgrade to 9.04..."
date: 2009-05-03
forum: General Help
---

### Post by JohnnySkidmark on 2009-05-03
I have a 64-bit [FONT="Courier New"]Ubuntu Server[/FONT] 8.10 host running [FONT="Courier New"]VMware Server[/FONT] 1.0.8.  One of the guests is a [FONT="Courier New"]Samba[/FONT] file server, which I believe started out running 64-bit [FONT="Courier New"]Ubuntu Server[/FONT] 7.04 or 7.10 and has been upgraded with each new release, so it now runs 8.10.  In addition to a disk for the root partition, it has five virtual SCSI disks for file storing different types of files.  The [FONT="Courier New"]/etc/fstab[/FONT] entries for those virtual disks look like this:
```
# Media drives
/dev/media-audio        /data/media/audio       ext3            defaults,rw,data=journal,relatime,user_xattr    0       2
/dev/media-graphics     /data/media/graphics    ext3            defaults,rw,data=journal,relatime,user_xattr    0       2
/dev/media-video        /data/media/video       xfs             defaults,relatime,rw                    0       2

# Temp drives
/dev/temp-graphics       /data/temp/graphics      reiserfs        defaults,relatime,rw,data=journal,user_xattr    0       2
/dev/temp-video          /data/temp/video         xfs             defaults,relatime,rw                    0       2
```

I have a [FONT="Courier New"]/etc/udev/rules.d/66-lvm-storage.rules[/FONT] file which creates the device names based on each disk's SCSI ID (the "lvm" is because the virtual disks are ultimately just exposing logical volumes on the host, but that should be just an implementation detail which isn't important here):
```
ACTION=="add", GOTO="lvm_storage_start"
GOTO="lvm_storage_end"

LABEL="lvm_storage_start"

ENV{ID_PATH}=="pci-0000:00:11.0-scsi-0:0:0:0", NAME="media-audio", GOTO="lvm_storage_end"
ENV{ID_PATH}=="pci-0000:00:11.0-scsi-0:0:1:0", NAME="media-graphics", GOTO="lvm_storage_end"
ENV{ID_PATH}=="pci-0000:00:11.0-scsi-0:0:2:0", NAME="media-video", GOTO="lvm_storage_end"
ENV{ID_PATH}=="pci-0000:00:12.0-scsi-0:0:1:0", NAME="temp-graphics", GOTO="lvm_storage_end"
ENV{ID_PATH}=="pci-0000:00:12.0-scsi-0:0:2:0", NAME="temp-video", GOTO="lvm_storage_end"

LABEL="lvm_storage_end"
```

This setup has worked perfectly for the last couple years.  The other day I upgraded the guest to 9.04 using the [FONT="Courier New"]cdromupgrade[/FONT] script on the [FONT="Courier New"]Ubuntu Server[/FONT] install CD.  Everything went smoothly and is working as it did before *except* when booting I get some "mount: special device /dev/*name* does not exist" errors.  I know some changes have been made to [FONT="Courier New"]udev[/FONT] and I've seen some people suggest that the syntax for rules files has changed, but I'm not sure that's what my problem is here.  If I run [FONT="Courier New"]udevadm test /sys/block/sd*x*[/FONT] (where *x* is b-f) then it does create the correct device file as expected.  So, I think my rules file is fine, it's just not being run properly during boot.

Also, I did five reboots in a span of about 20 minutes, and each time a different group of device files were missing: [FONT="Courier New"]temp-graphics[/FONT] was missing every time, [FONT="Courier New"]media-graphics[/FONT] was missing four times, [FONT="Courier New"]media-audio[/FONT] was missing three times, and [FONT="Courier New"]media-video[/FONT] and [FONT="Courier New"]temp-video[/FONT] were never missing (both are XFS filesystems, coincidentally).  To me, that looks like a timing issue or a race condition or something.  I tried renaming my rules file from [FONT="Courier New"]66-lvm-storage.rules[/FONT] to [FONT="Courier New"]99-lvm-storage.rules[/FONT] but that didn't seem to fix anything.  I would also point out that early in the boot sequence I see a "sd x:0:0:0: [sdx] Assuming drive cache: write through" message for each of the six virtual disks, so it *does* see the drives well before it tries to mount them, it's just [FONT="Courier New"]udev[/FONT] isn't reliably working its magic for some reason.  Any ideas?

---

