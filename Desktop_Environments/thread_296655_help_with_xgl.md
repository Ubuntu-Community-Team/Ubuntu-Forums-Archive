---
title: "help with xgl"
date: 2006-11-09
forum: Desktop Environments
---

### Post by flclisgreat on 2006-11-09
i need help installing xgl in ubuntu edgy eft,i used the wikki guide [here]("http://ubuntuguide.org/wiki/Ubuntu:Edgy") but now i am stuck. i get to where i am saposed to install xgl/compiz with ```
sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome
sudo cp /etc/gdm/gdm.conf-custom /etc/gdm/gdm.conf-custom-backup
gksudo gedit /etc/gdm/gdm.conf-custom
``` 

but when i do i get  
```
server-xorg libglitz-glx1 compiz-gnome
Reading package lists... Done
Building dependency tree
Reading state information... Done
Note, selecting libgl1-mesa-glx instead of libgl1-mesa
libgl1-mesa-glx is already the newest version.
xserver-xorg is already the newest version.
The following extra packages will be installed:
compiz-core compiz-plugins libglitz1 libxcomposite1
Recommended packages:
cgwd
The following NEW packages will be installed:
compiz compiz-core compiz-gnome compiz-plugins libglitz-glx1 libglitz1
libxcomposite1 xserver-xgl
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 2439kB of archives.
After unpacking 8073kB of additional disk space will be used.
Do you want to continue [Y/n]?
```

if i tried y,Y,yes,Yes then enter and it aborts. any idea's?

---

### Post by John.Michael.Kane on 2006-11-10
Have a read [http://www.ubuntuforums.org/showthread.php?t=263851&highlight=beryl](http://www.ubuntuforums.org/showthread.php?t=263851&highlight=beryl)

---

### Post by rsambuca on 2006-11-10
I have had similar problems in the past.  I think you have to enter the command lines of code in separately (at least that is what I did) and it should let you input the "y" for yes.  Then you can enter the second line of code, then the third, etc.

---

