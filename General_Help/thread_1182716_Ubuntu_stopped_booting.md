---
title: "Ubuntu stopped booting"
date: 2009-06-09
forum: General Help
---

### Post by joehte on 2009-06-09
Hi,

I can't anymore boot to my Ubuntu because for some reason my /var partition does not get mounted upon boot. I can access the command-line but the Gnome environment won't start since it can't access /var/lib/gdm, obviously because /var can not be mounted.

I'm using lvm and it seems the /var partition has for some reason lost its UUID and the partition does not identify itself as ext3 anymore but something weird instead. Seems like there's been some kind of corruption although I don't understand how.

Anyway I can mount /var just fine if I specify manually the filesystem type to be ext3:

```
sudo mount -t ext3 /dev/mapper/vg-var /var
```

And from /etc/fstab I can see what the UUID is supposed to be.

Now my question is how can I set again the UUID and filesystem type without wiping my precious /var partition? Obviously I would like to know how it got corrupted in the first place but that might be difficult. Right now I just want it to work again.

Please help.

---

### Post by zaresar on 2009-06-09
hey try edditung ur grab
or try logging wid recovery mode

---

### Post by zvacet on 2009-06-09
```
blkid
```

and see if UUID match one from fstab.If not then change UUID in fstab with one you get from **blkid** command.

---

### Post by joehte on 2009-06-09
> **zvacet said:**
> ```
blkid
```

and see if UUID match one from fstab.If not then change UUID in fstab with one you get from **blkid** command.

Like I said the partition has totally lost it's UUID and the filesystem type is wrong. My question was how can I change the filesystem type to correct one and set the UUID?

---

