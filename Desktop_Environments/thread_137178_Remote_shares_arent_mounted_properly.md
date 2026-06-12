---
title: "Remote shares arent mounted properly"
date: 2006-02-27
forum: Desktop Environments
---

### Post by ashrack on 2006-02-27
sometimes when I do
```
sudo mount -a
```
I don't get the LINK to desktop for my remote share although the share is mounted. So I must do the following:
```
sudo umount /media/d
```
and then again do:
```
sudo mount -a
```
to get the link to desktop

my fstab:
[ATTACH]6485[/ATTACH]

---

### Post by claes on 2006-02-27
Could be that the desktop don't refresh as it should. Instead of umount and mount try and press ctrl+r and se if the mounts apear.

Claes

---

### Post by ashrack on 2006-02-27
[QUOTE=claes]Could be that the desktop don't refresh as it should. Instead of umount and mount try and press ctrl+r and se if the mounts apear.

Claes[/QUOTE]
good idea. will try it when it happens again

---

### Post by ashrack on 2006-03-15
[QUOTE=claes]Could be that the desktop don't refresh as it should. Instead of umount and mount try and press ctrl+r and se if the mounts apear.

Claes[/QUOTE]
after two weeks it again happened. So I tried CTRL+R but it does nothing.
so I still had to do the following to get the ICON for the network share
```
sudo umount /media/d
sudo mount -av
```

---

### Post by ashrack on 2006-03-16
any ideas why it wont automaticli put the ICON on the gnome desktop?

---

