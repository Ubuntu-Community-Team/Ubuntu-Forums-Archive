---
title: "Re-enabling GDM"
date: 2007-07-26
forum: Desktop Environments
---

### Post by Grangersam on 2007-07-26
I was editing the active services and accidentally removed gdm from the start-up
One the computer starts, it brings me to a login in the terminal

I have tried many things including:

CRTL-ALT-F7
Startx
Sudo apt-get install - reinstall gdm  (which resulted in a an error saying that there was no file to install)
Sudo /etc/init.d/gdm start

If you have any more ideas about how to enable the GDM, they will be greatly appreciated

---

### Post by obrient on 2007-07-26
First I would see if you have it installed. gdm --version. Then I would try to run the following
```
sudo gdmsetup
``` and see if that works. Also check to see if you have a gdm.conf file in the/etc/X11/gdm folder. Funny that sudo apt-get install gdm didn't fix it.

---

### Post by Grangersam on 2007-07-27
'sudo gdmsetup' returned:

(gdmsetup: 5010): Gtk-WARNING **: cannot open display

Still doesn't work
And how do I check to see if i have that file?

---

### Post by obrient on 2007-07-27
First I would check to see if gdm is installed by doing ```
gdm --version
``` then to see if you have the files needed do a ```
cd /etc/X11/gdm
``` then ```
ls -alh
``` to list the files. You should have a gdm.conf and a gdm.conf-custom file.

Also what did you get as output when you do a ```
sudo startx
```?

---

### Post by tbroderick on 2007-07-27
```
sudo dpkg-reconfigure gdm
```

Might work.

---

