---
title: "No GUI"
date: 2006-09-22
forum: Desktop Environments
---

### Post by shootdamonkey on 2006-09-22
I messed around with compiz and now i have no gui cos x cant start, i am in need of a way to repair ubuntu withought fully re-installing it.

---

### Post by shootdamonkey on 2006-09-22
soz forgot to post my error:

```
GDM: Xserver not found: usr/local/bin/xgl :0 :0 -fullscreen -ac -accel xv -accel glx:pbuffer -auth /var/lib/gdm/:0.xauth -nolisten tcp vt7

Error: Command could not be executed!

Please install the xserver or correct GDm configuration and restart gdm

```

---

### Post by Paul41 on 2006-09-22
Do you remember what changes you made?  I think you could use nano at the command prompt to change things back.  Type
```
nano you_file_name
```
at the command prompt.  Or
```
sudo nano you_file_name
```
if you need sudo privlidges.

---

### Post by Rashid584 on 2006-09-22
I think you should delete the .desktop file you created from the HOWTO/wiki/whatever you followed.

Part of it is creating a .desktop file somewhere...look on the howto you followed, find where it is, and delete it/rename it from the command line.

```
rm filename
```

to delete

```
mv filename
```

to rename.

Hope that helps.

-Rashid

---

