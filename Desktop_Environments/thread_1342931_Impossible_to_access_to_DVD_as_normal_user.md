---
title: "Impossible to access to DVD as normal user"
date: 2009-12-01
forum: Desktop Environments
---

### Post by manolomanolo on 2009-12-01
Hi to all.

I can do access to my DVD in case of connecting as root but I'm unable to do it when I connect as normal user. Actually I access the DVD running
```
sudo nautilus
```
and selecting the /media/DVD_VIDEO_RECORDER folder, otherwise that folder is not even listed by nautilus.

I've been controlling that this normal user has got all the privileges, incuding "Use CDROM drives", listed into the

System -> Administration -> Users & Groups -> (select the user) -> Proprerty -> Advanced

Also unchecked and checked back the "Use CDROM drives" option (yes, I know... windows way solution...) but nothing changed.

Any suggestion, please?
Thank you.

---

### Post by nerdy_kid on 2009-12-01
posting to say you shouldnt run graphical programs with sudo -- use gtksu instead.  Else permissions get messed up...which sounds like what happened.  sorry i cant help anymore.

---

### Post by manolomanolo on 2009-12-01
**UPDATE 1**: running
```
gksu nautilus
``` seems to produce the same effects than ```
sudo nautilus
```

**UPDATE 2**: the ***mtab*** line related to my DVD drive

```
/dev/sr0 /media/DVD_VIDEO_RECORDER udf ro,nosuid,nodev,uhelper=devkit,uid=1000,gid=1000,iocharset=utf8,umask=0077 0 0
```

where 1000 is the uid and gid of that normal user. On the other hand, ***fstab*** has no line related to DVD and any other removable drive.

**UPDATE 3**: using Karmic Koala, kernel 2.6.31-15-generic

---

### Post by nerdy_kid on 2009-12-01
> **manolomanolo said:**
> **UPDATE 1**: running
```
gksu nautilus
``` seems to produce the same effects than ```
sudo nautilus
```**UPDATE 2**: the ***mtab*** line related to my DVD drive

yes i know, but it (can) fry your permissions.  root ends up owning files in you $HOME folder which causes a big mess...other people can give more details about it.


[edit]

it sounds like your permissions are busted -- which is beyond my skill to repair.  i would create a new user and see if it works from there...

---

