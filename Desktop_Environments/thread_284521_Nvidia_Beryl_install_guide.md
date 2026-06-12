---
title: "Nvidia Beryl install guide"
date: 2006-10-25
forum: Desktop Environments
---

### Post by SC2Sick on 2006-10-25
I noticed that there is not a documented straight forward install of the XGL/Beryl environment for the Nvidia platform..  so after struggling to find the information on a couple of occasions...  I decided to write one for myself and others to use.

Firstly.. make sure that you have the correct repositories..

the most current list can be found at
[http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories)

----------------------------------------------------------
Secondly make sure you have the Nvidia driver installed.  Xgl will not work without it.

from the terminal:
```
sudo apt-get install nvidia-glx nvidia-kernel-common
```

once that is finished:
```
sudo nvidia-xconfig
```

----------------------------------------------------------
Third, edit the sources list to include the XGL/Beryl repositories

from terminal:
```
sudo gedit /etc/apt/souces.list
```

add these to the end of the file.

#Beryl Repositories for Dapper Drake (Ubuntu 6.06)
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb-src [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main

save the file.  the from terminal :
```
wget [http://www.beerorkid.com/compiz/quinn.key.asc](http://www.beerorkid.com/compiz/quinn.key.asc) -O - | sudo apt-key add -
KEY=81836EBF; gpg --keyserver subkeys.pgp.net --recv $KEY && gpg --export --armor $KEY | sudo apt-key add -
```

(include all of that into one command)

from terminal:
```
sudo apt-get update
```
(optional but recommended step)
```
sudo apt-get dist-upgrade
```

--------------------------------------------------------------------
Installing Beryl

from terminal:
```
sudo apt-get install xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 beryl emerald-themes
```

_________________________________________________
Setting up XGL and Beryl to launch from GDM

from terminal:
```
sudo gedit /usr/bin/startxgl.sh
```

paste the following into the file
```

#!/bin/sh
 Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:1
 # Start GNOME
exec gnome-session
```


save the file

then from terminal:
```
sudo chmod 755 /usr/bin/startxgl.sh
```

then from terminal:
```
sudo gedit /usr/share/xsessions/xgl.desktop
```

paste in the following:

```
[Desktop Entry]
Encoding=UTF-8
Name=XGL
Exec=/usr/bin/startxgl.sh
Icon=
Type=Application


```----------------------------------------------------
Last set the environment to automatically start when you login to xgl from GDM

In Gnome:	System->Preferences->Sessions->Startup Programs and add the following:

gnome-settings-daemon
beryl-manager
xmodmap -e "keycode 22 = BackSpace"



reboot and under options in GDM change the session to XGL

---

