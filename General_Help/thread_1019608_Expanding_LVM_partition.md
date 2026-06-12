---
title: "Expanding LVM partition"
date: 2008-12-23
forum: General Help
---

### Post by MrE on 2008-12-23
I ran out of drive space on my Ubuntu server, and since there is no room for a second hard drive (it's an old Dell Optiplex GX270), I used Clonezilla to clone the drive onto a bigger one.

This worked great but now I'd like to add the free space to my LVM partition so that I can expand the PV.

To clarify, what I'm trying to do is the same as one would do to expand an ext3 partition, the only difference being that I need to do this on an LVM type partition i.e. at a much lower level, before LVM itself comes into play,. This is *not* the same as resizing a VG, PV or LV! 

The following table probably illustrates it better:

```
 Name                 Flags                Part Type         FS Type                       [Label]                   Size (MB)
 ---------------------------------------------------------------------------------------------------------------------------------------------
       sda1                                       Primary          Linux ext3                                                 106.93
       sda2                                       Primary          Linux                                                      148.06
       sda5                                       Logical          Linux LVM                                                19740.68
                                                  Pri/Log          Free Space                                               20003.89
```

What is the best way to go about this?

---

### Post by hyper_ch on 2008-12-23
my howto partially covers your question. Have a look here:

[http://www.howtoforge.com/set-up-a-fully-encrypted-raid1-lvm-system-p7](http://www.howtoforge.com/set-up-a-fully-encrypted-raid1-lvm-system-p7)

---

