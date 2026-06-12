---
title: "Looking Glass on Kubuntu"
date: 2007-03-05
forum: Desktop Environments
---

### Post by Muis24 on 2007-03-05
Are there any kubuntu users around that have succesfully installed and are using Project Looking Glass as the default window manager? I just wondered if it would be posible, because LG just looks great and I really want to install it in my system as well, however, when I read other post regarding LG, there seem to be quite some problems with using and installing it. Could somebody please help me out? ;)

---

### Post by wxnker on 2007-03-11
I'm running it on Kubuntu Feisty herd 5 (with no GDM) and it works okay considering that it's still in an infant stage of development.
I use KDE as default but at login I can choose "Looking glass" instead to try it out (just like if you were starting a gnome session before "log in"). 
So it does not create any problems with my Kubuntu.

It's far from perfect yet, but it works and it isn't as slow on my Nvidia Geforce FX5500 256 MB as I expected.

_First test if OpenGl works:_
```
glxinfo | grep version
[COLOR="Gray"]result: opengl version string: 2.1.0 NVIDIA 97.46[/COLOR]

glxinfo | grep direct
[COLOR="Gray"]result: direct rendering: Yes[/COLOR] 
```

_If you have OpenGL working then install the stable version by adding this repository in adept or your sources.list:_

deb [http://javadesktop.org/lg3d/debian](http://javadesktop.org/lg3d/debian) stable contrib

[U]
For other repositories:[/U]
[http://www.ubuntuforums.org/showpost.php?p=2137802&postcount=6](http://www.ubuntuforums.org/showpost.php?p=2137802&postcount=6)

I used "aptitude install" but you can use Adept or "apt-get install" if you want.

```
sudo aptitude update
sudo aptitude install lg3d-core
```

Regards
Wxnker```

```

---

### Post by kystorms on 2007-09-20
okay, if we load it and find out its just to much for our system how can we remove it and the programs that came with it?
:confused:

---

### Post by mustang50 on 2007-10-31
Im having problems installing Looking Glass is there a way to work though it or should i just compile it myself?


root@mustang50187-laptop:/home/mustang50187# sudo apt-get install lg3d-core
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  lg3d-core
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 65.5MB of archives.
After unpacking 0B of additional disk space will be used.
WARNING: The following packages cannot be authenticated!
  lg3d-core
Install these packages without verification [y/N]? y
Get:1 [http://javadesktop.org](http://javadesktop.org) unstable/contrib lg3d-core 1.0.1_dev [65.5MB]
Fetched 65.5MB in 5m44s (190kB/s)
(Reading database ... 383157 files and directories currently installed.)
Unpacking lg3d-core (from .../lg3d-core_1.0.1%5fdev_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/lg3d-core_1.0.1%5fdev_i386.deb (--unpack):
 subprocess pre-installation script returned error exit status 10
Errors were encountered while processing:
 /var/cache/apt/archives/lg3d-core_1.0.1%5fdev_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)[http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif)

---

