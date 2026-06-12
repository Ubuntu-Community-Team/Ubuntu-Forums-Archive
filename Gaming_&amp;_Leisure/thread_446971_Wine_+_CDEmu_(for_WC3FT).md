---
title: "Wine + CDEmu (for WC3FT)"
date: 2007-05-17
forum: Gaming &amp; Leisure
---

### Post by celiothrkn on 2007-05-17
I am trying to run Warcraft III FT on Wine. The game installed properly. So did CDEmu. I mount an image of the game CD onto CDEMu.
```
$ cdemu -s
Drive Loaded Comment
  0:     1   Warcraft III.mds
  1:     0   NO_CD_LOADED
  2:     0   NO_CD_LOADED
  3:     0   NO_CD_LOADED
  4:     0   NO_CD_LOADED
  5:     0   NO_CD_LOADED
  6:     0   NO_CD_LOADED
  7:     0   NO_CD_LOADED
```

Under "winecfg," I set /dev/cdemu0 (the mount point, I believe) as my D:/. I get the following error message.
```
$ winecfg
err:winecfg:load_drives GetVolumeInformation() for 'D:\' failed, setting serial to 0
```

When I list /dev/cdemu0, I get nothing.
```
$ ls /dev/cdemu0
/dev/cdemu0
```

Any idea why it would fail?

---

### Post by ebichu on 2007-05-17
I belive you need to mount it first: mount /dev/cdemo0 /media/image, for example.
/dev/... should be just a device.

---

### Post by celiothrkn on 2007-05-18
I mounted my /dev/cdemu0 into /mnt/iso and set my winecfg's D:/ as /mnt/iso but winecfg failed on me.

```
$ ls /mnt
iso

$ sudo mount -t iso9660 /dev/cdemu0 /mnt/iso
mount: block device /dev/cdemu0 is write-protected, mounting read-only

$ winecfg
err:winecfg:load_drives GetVolumeInformation() for 'D:\' failed, setting serial to 0
```

---

### Post by Enverex on 2007-05-18
Just use the CD-drive as normal, it will work fine, don't bother with disc images, especially with CDEmu.

---

### Post by fire_lock on 2010-07-12
I had a similar problem. I solve it with installing AcetoneISO2. I mounted the image. Than saw the mounted drive. Than in wine config I entered new drive as CD and I added the path to the mounted drive. It worked perfectly :)

---

### Post by ELD on 2010-07-12
OMG necro!

---

### Post by Iowan on 2010-07-12
Closed - R.I.P

---

