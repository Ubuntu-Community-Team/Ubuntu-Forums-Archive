---
title: "Removing Desktop Icon and Places Entry for USB Hard Drive"
date: 2008-05-06
forum: Desktop Environments
---

### Post by AustinMatherne on 2008-05-06
Hi, I added a second hard drive (300GB External USB) to my Xubuntu 8.04 installation, using the following commands.

```
sudo mkdir /home/austin/Media
```
```
sudo mount /dev/sda1 /home/austin/Media
```
I then added this line to the the bottom of /etc/fstab:
```
/dev/sda1    /home/austin/Media   ext3    defaults     0        0
```

Problem is I still have an entry in the places menu for "320G Volume" that I would really like to delete or at lest hide.

I also still have a "320G Volume" icon on my desktop, I can hide it by going to "Applications > Settings > Settings Manager > Desktop" and removing the check mark in the "removable devices" box under the "Behavior" tab.  This also removes any icons on my desktop for any other removable devices, which I really don't want to do.

Anyone know another way to do this?

Thanks,
~ Austin

---

### Post by amohanty on 2008-05-06
Fire up gconf-editor form the terminal:
gconf-editor &

Then drill down to this key:
/apps/nautilus/desktop/

uncheck volumes_visible on the right side pane.

hth
am

---

### Post by everlasting.void on 2008-09-15
I installed gconf and did as instructed (/apps/nautilus/desktop/) but when gconf_editor comes up I dont have nautilus under apps.  What I do have is bug-buddy and gconf-editor.

---

### Post by HacDan on 2008-09-15
You are using Xubuntu, your filemanager isn't Nautilus, so you won't have settings in gconf-editor for applications that aren't installed. The said solution would not solve what you are trying to do anyways. The solution will remove the icons, but also for any new device plugged in like a thumb drive, the icon will not show. Same goes the Places Menu

---

### Post by aomlives on 2008-09-16
> **AustinMatherne said:**
> Problem is I still have an entry in the places menu for "320G Volume" that I would really like to delete or at lest hide.

I also still have a "320G Volume" icon on my desktop, I can hide it by going to "Applications > Settings > Settings Manager > Desktop" and removing the check mark in the "removable devices" box under the "Behavior" tab.  This also removes any icons on my desktop for any other removable devices, which I really don't want to do.

[URL="http://ubuntuforums.org/showthread.php?t=393861"]
This [/URL]thread handles your problem. Looks like you have to mount your "320G Volume" in any other than your /media directory (by editing the fstab entry), because all volumes mounted there will show up automagically on your desktop. For example mount your new hard drive in /mnt or your home folder, then reboot, and the desktop icon and places entry should be gone.

Hope this helps.

---

