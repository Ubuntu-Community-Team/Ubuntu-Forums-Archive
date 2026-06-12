---
title: "mounting remote shares..."
date: 2009-01-12
forum: Desktop Environments
---

### Post by pcal on 2009-01-12
Sorry guys if this is a bit too noob, but I've found lots of posts that don't quite answer my issue...

I have 2 different, but related problems. I want to set up Firefox and Thunderbird under v8.10 to use profiles in common with the equivalent software installed in the XP partition of a dual boot machine.

The firefox profile is in the XP partition. I can mount the XP partition via the Places/Computer menu, and once mounted, FF works just fine with this profile. What I can't figure, is how to tell Ubuntu to automatically mount this partition at boot. (I've seen much argument over the pro's and con's of editing fstab, but feel a gui option would be better if it exists.)

The Thunderbird profile is on a NAS device on my lan (with thousands of e-mails). Again, I can manually mount this share via the Places/Network menu. I can't figure how to auto mount this one either, but in addition - even when it is mounted - can't get TB to recognise it as a valid location from which to read the profile.

Where have I failed to look for an appropriate option...

Thanks in anticipation,

Pcal

---

### Post by taurus on 2009-01-12
Install ntfs-config and use it to configure your ntfs partition.

Applications -> Accessories -> Terminal
```
sudo apt-get update
sudo apt-get install ntfs-config
gksudo ntfs-config
```

---

### Post by pcal on 2009-01-16
Thanks Taurus. That solved the first problem very easily.

Regards,

Pcal

---

### Post by jure1873 on 2009-01-17
to mount nfs put this in /etc/fstab
<server>:</path/of/dir> </local/mnt/point> nfs <options> 0 0

put auto in <options> to get it mounted automatically at startup

For the tb profile you can link the directory on the mount point to your local tb installation or modify ~/.mozilla-thunderbird/profiles.ini and put your profile on nfs there

[Profile1]
Name=ProfileNAS
IsRelative=0
Path=/mnt/nfsshare/thunderbird/uwtho2ab.default
Default=1

---

