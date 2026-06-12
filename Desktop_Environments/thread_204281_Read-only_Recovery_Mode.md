---
title: "Read-only Recovery Mode?"
date: 2006-06-26
forum: Desktop Environments
---

### Post by Lester King on 2006-06-26
I was messing around with my xorg.conf file and I have somehow ruined it. 

The good news is that before I began doing that I backed up my original xorg.conf file. Now my only issue is that I can't seem to get to any sort of command line that will allow me to copy my backup file over the broken .conf file and fix the issue. What am I missing? I've tried the liveCD, I've tried the sudo-ing without loading X, I've tried logging in as root and I can't seem to get read/write access to this file. Why is "recovery mode" a read-only system?

---

### Post by aysiu on 2006-06-26
Recovery mode isn't a read-only system.
Recovery mode logs you in as root.
Assuming you named your file xorg.conf_backup, you would simply do this ```
cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

---

### Post by vidak on 2006-06-27
[QUOTE=aysiu]Recovery mode isn't a read-only system.
Recovery mode logs you in as root.
Assuming you named your file xorg.conf_backup, you would simply do this ```
cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```[/QUOTE]

if you get an error 'read-only filesystem' you could try
mount /dev/hda1 -o rw,remount
or whatever your drive is...

---

### Post by Lester King on 2006-06-27
[QUOTE=aysiu]Recovery mode isn't a read-only system.
Recovery mode logs you in as root.
Assuming you named your file xorg.conf_backup, you would simply do this ```
cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```[/QUOTE]

That's exactly what I did. I received an error saying that it was a read-only system. 

Luckily, I was able to remount the harddrive and go from there. 
Thanks for your help.

---

