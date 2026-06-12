---
title: "lost my desktop Please help"
date: 2007-03-29
forum: Desktop Environments
---

### Post by mrreality13 on 2007-03-29
Ok I tried the Envy gui then "poof" black screen ,(for a 5200)
now when i try the
"sudo dpkg-reconfigure xserver-xorg"

Ive tried 4 different settings and cant get my desk top back any ideas??
](*,)  i really don't want to do a reinstall...](*,) 
thanx in advance

---

### Post by tho on 2007-03-30
> **mrreality13 said:**
> Ok I tried the Envy gui then "poof" black screen ,(for a 5200)
now when i try the
"sudo dpkg-reconfigure xserver-xorg"

Ive tried 4 different settings and cant get my desk top back any ideas??
](*,)  i really don't want to do a reinstall...](*,) 
thanx in advance

nvidia-xconfig automatically makes backups of /etc/X11/xorg.conf. They should be named xorg.conf.bak or xorg.conf_backup_YYYYMMDDHHMM. Simply move the backup over the automatically generated one.

---

### Post by mrreality13 on 2007-03-30
ok ill try but move how??

---

### Post by NikoC on 2007-03-31
cd /etc/X11
ls      --> find the name of the xorg backup file made by nvidia e.g. xorg.backup.YYYYMMDDHHMM
sudo cp xorg.backup.YYYYMMDDHHMM xorg.conf

This will replace your newly generated xorg file by the old one and still keeps the backup.

---

### Post by mrreality13 on 2007-03-31
i enter the"cd /etc/X11" in a terminal i assume?

YYYYMMDDHHMM and this i assume i look for the recent one for "year month day hour minute"?

and replace the most recent with the older?

---

