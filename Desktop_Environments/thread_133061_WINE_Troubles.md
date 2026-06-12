---
title: "WINE Troubles"
date: 2006-02-19
forum: Desktop Environments
---

### Post by SVFUSiON on 2006-02-19
I can not seem to get WINE working right, it was until i messed it up :cool: Is there a way I can COMPLETLY remove wine and the configs?

here is what it is doing right now,

[IMG]http://www.fusionlan.com/Screenshot.png[/IMG]

---

### Post by lha on 2006-02-19
If the only thing you messed up are those partition letter mappings, why don't you clean them up (rm ~/.wine/dosdevices/*) and recreate them? For example,
ln -s ~/.wine/drive_c ~/.wine/dosdevices/c\:
ln -s /media/cdrom0 ~/.wine/dosdevices/d\:

---

### Post by SVFUSiON on 2006-02-19
that worked! thanks. do you know how I can access the fake windows directory from the file browser?

---

### Post by lha on 2006-02-19
.wine is hidden (caused by that dot), so nautilus wont show it unless you tell it to do so. (Press <control>-H) You can also make a symlink to that directory
```
ln -s ~/.wine/drive_c ~/fake_windows
```
**or** move the actual directory and change drive mappings:
```
mv ~/.wine/drive_c ~/fake_windows
rm ~/.wine/dosdevices/c\:
ln -s ~/fake_windows ~/.wine/dosdevices/c\:
```

---

