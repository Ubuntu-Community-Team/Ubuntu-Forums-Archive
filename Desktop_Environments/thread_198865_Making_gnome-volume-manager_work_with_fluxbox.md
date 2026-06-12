---
title: "Making gnome-volume-manager work with fluxbox"
date: 2006-06-17
forum: Desktop Environments
---

### Post by princemackenzie on 2006-06-17
My main issue in not being able to convert to fluxbox full time from GNOME is that I can not find a way to make the gnome-volume-manager show up easily on the fluxbox desktop.  I would really like to disconnect my iPod easily as well as have quick access to the CD-Rs and such I use.  Any help you could provide in having some program like this would be great!

---

### Post by mlind on 2006-06-17
[QUOTE=princemackenzie]My main issue in not being able to convert to fluxbox full time from GNOME is that I can not find a way to make the gnome-volume-manager show up easily on the fluxbox desktop.  I would really like to disconnect my iPod easily as well as have quick access to the CD-Rs and such I use.  Any help you could provide in having some program like this would be great![/QUOTE]

I don't know about such program, but if you need ipod to mount automatically
try this.

create new rule for ipod
```

sudo touch /etc/udev/rules.d/60-ipod.rules
echo 'BUS="scsi", SYSFS{model}="iPod*", KERNEL="sd?2", SYMLINK+="ipod"' | sudo tee -a /etc/udev/rules.d/60-ipod.rules
mkdir -p /media/ipod

```

This will create symlink /dev/ipod that points to your ipod device when udev
is next time restarted. If you're having problems, try using filename **10**-ipod.rules instead

Then edit /etc/fstab, and insert line
```

/dev/ipod       /media/ipod           vfat    rw,user,noauto          0       0

```

After this, restart udev
```

sudo /etc/init.d/udev restart

```

Check that udev creates /dev/ipod node. Try pluggin your ipod and see if it
is accessible using /dev/ipod and if it mounts automatically.

---

### Post by princemackenzie on 2006-06-17
[QUOTE=mlind]I don't know about such program, but if you need ipod to mount automatically
try this.

create new rule for ipod
```

sudo touch /etc/udev/rules.d/60-ipod.rules
echo 'BUS="scsi", SYSFS{model}="iPod*", KERNEL="sd?2", SYMLINK+="ipod"' | sudo tee -a /etc/udev/rules.d/60-ipod.rules
mkdir -p /media/ipod

```

This will create symlink /dev/ipod that points to your ipod device when udev
is next time restarted. If you're having problems, try using filename **10**-ipod.rules instead

Then edit /etc/fstab, and insert line
```

/dev/ipod       /media/ipod           vfat    rw,user,noauto          0       0

```

After this, restart udev
```

sudo /etc/init.d/udev restart

```

Check that udev creates /dev/ipod node. Try pluggin your ipod and see if it
is accessible using /dev/ipod and if it mounts automatically.[/QUOTE]

Thanks for your help, but my ipod does mount automatically...

I was just looking for a desktop icon or somesuch where i could get easy access to it or the other drives I mount (like my windows drive and my shared fat32 drive).  In GNOME, there are easy links to these on the desktop.  I was just trying to find a way to get this kind of icon access on the fluxbox desktop.

---

### Post by mlind on 2006-06-17
If you're willing to use gnome-volume-manager, try if these instructions still apply.
Atleast the gnome-volume-manager part [http://www.ubuntuforums.org/showpost.php?p=107269&postcount=11](http://www.ubuntuforums.org/showpost.php?p=107269&postcount=11)

---

