---
title: "newbie in recovery"
date: 2006-01-19
forum: Desktop Environments
---

### Post by ubuntu irv on 2006-01-19
I am booted into recovery as I changed some setting for the mouse in xorg,conf and now the machine will not boot to desktop.  I am sitting at root@ubuntuirv;~#
Could someone help me?

---

### Post by darth_vector on 2006-01-19
run the following```
dpkg-reconfigure -phigh xserver-xorg
/etc/init.d/gdm start
```

post back if that doesnt work.

---

### Post by ubuntu irv on 2006-01-20
Thanks a lot.
What happens is  before I finish typing it, it comes back psmouse.C: bad data from KBC - timeout.I hit enter and it comes back /usr/sbin/dpkg-reconfigure: please specify a package to reconfigure

---

### Post by darth_vector on 2006-01-20
can you run any commands at all? if you can, and you can remember what you changed in /etc/X11/xorg.conf you can change it back and then```
/etc/init.t/gdm start
```or```
/etc/init.d/gdm restart
```depending on how terminal the edit was to gnome.

is the machine connected to the internet by the way?

---

### Post by ubuntu irv on 2006-01-20
yes it connected by cable.  I know exactly what I changed, but can't get to it

---

### Post by darth_vector on 2006-01-20
if you are on a laptop this error can be caused by touching the touchpad or the mouse (apparently). try typing without touching the mouse.

---

### Post by ubuntu irv on 2006-01-20
Yes, I am on a laptop.
When I type it in I get /etc/X11/xorg.conf:  Permission denied

---

### Post by darth_vector on 2006-01-20
ok. i think you arent in recovery mode - you are in a virtual terminal. try using sudo```
sudo dpkg-reconfigure -phigh xserver-xorg
sudo /etc/init.d/gdm start
```

to get into recovery mode you have to restart the computer and select recovery mode in the grub menu (hold down ESC on boot if you have the hiddenmenu option enabled). this should not be necessary for the time being.

---

### Post by ubuntu irv on 2006-01-20
Thank YOU!!!:p 

It booted to the desktop.
I went in and makde the change back to the way it was and saved it.  Its rebooting now.....

---

### Post by darth_vector on 2006-01-20
no worries mate. have a nice weekend ;-)

---

### Post by ubuntu irv on 2006-01-20
:KS :) It worked!!

THANK YOU!

---

