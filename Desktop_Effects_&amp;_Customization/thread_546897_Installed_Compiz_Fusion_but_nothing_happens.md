---
title: "Installed Compiz Fusion but nothing happens?"
date: 2007-09-09
forum: Desktop Effects &amp; Customization
---

### Post by AlexTepes on 2007-09-09
I checked similar posts but they don't have the same issues.
I useds the Auto installer script I think, first it removed everything and didn't install the icon correctly.
Rebooted, tried again.
I got the Icon and Compiz Fusion manager in the System area.
But nothing happens when I click it.
I looked at other posts and they say

compiz --indirect-rendering --replace -c emerald

And commands like it, and I get:

bash: compiz: command not found

But it did install, I even tried twice, somethings not going right here, any suggestions?

Here are some things:
alex@alex-desktop:~$ sudo apt-get install git git-core compiz-dev
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
git-core is already the newest version.
E: Couldn't find package compiz-dev


---Tried this:

alex@alex-desktop:~$ git-clone git://anongit.opencompositing.org/users/crdlb/fusion-icon
remote: Generating pack...
remote: Done counting 330 objects.
remote: Deltifying 330 objects...
remote:  100% (330/330) done
Indexing 330 objects.
remote: Total 330 (delta 172), reused 0 (delta 0)
 100% (330/330) done
Resolving 172 deltas.
 100% (172/172) done
alex@alex-desktop:~$ cd fusion-icon
alex@alex-desktop:~/fusion-icon$ make
running build
running build_py
creating build
creating build/lib
creating build/lib/FusionIcon
copying FusionIcon/__init__.py -> build/lib/FusionIcon
copying FusionIcon/data.py -> build/lib/FusionIcon
copying FusionIcon/environment.py -> build/lib/FusionIcon
copying FusionIcon/execute.py -> build/lib/FusionIcon
copying FusionIcon/interface.py -> build/lib/FusionIcon
copying FusionIcon/parser.py -> build/lib/FusionIcon
copying FusionIcon/start.py -> build/lib/FusionIcon
copying FusionIcon/util.py -> build/lib/FusionIcon
creating build/lib/FusionIcon/interface_qt4
copying FusionIcon/interface_qt4/__init__.py -> build/lib/FusionIcon/interface_qt4
copying FusionIcon/interface_qt4/main.py -> build/lib/FusionIcon/interface_qt4
creating build/lib/FusionIcon/interface_gtk
copying FusionIcon/interface_gtk/__init__.py -> build/lib/FusionIcon/interface_gtk
copying FusionIcon/interface_gtk/main.py -> build/lib/FusionIcon/interface_gtk
running build_scripts
creating build/scripts-2.4
copying and adjusting fusion-icon -> build/scripts-2.4
changing mode of build/scripts-2.4/fusion-icon from 644 to 755
alex@alex-desktop:~/fusion-icon$ make install
running install
running build
running build_py
running build_scripts
running install_lib
copying build/lib/FusionIcon/__init__.py -> /usr/lib/python2.4/site-packages/FusionIcon
error: could not delete '/usr/lib/python2.4/site-packages/FusionIcon/__init__.py': Permission denied
make: *** [install] Error 1
alex@alex-desktop:~/fusion-icon$ sudo make install
running install
running build
running build_py
running build_scripts
running install_lib
copying build/lib/FusionIcon/__init__.py -> /usr/lib/python2.4/site-packages/FusionIcon
copying build/lib/FusionIcon/data.py -> /usr/lib/python2.4/site-packages/FusionIcon
copying build/lib/FusionIcon/environment.py -> /usr/lib/python2.4/site-packages/FusionIcon
copying build/lib/FusionIcon/execute.py -> /usr/lib/python2.4/site-packages/FusionIcon
copying build/lib/FusionIcon/interface.py -> /usr/lib/python2.4/site-packages/FusionIcon
copying build/lib/FusionIcon/parser.py -> /usr/lib/python2.4/site-packages/FusionIcon
copying build/lib/FusionIcon/start.py -> /usr/lib/python2.4/site-packages/FusionIcon
copying build/lib/FusionIcon/util.py -> /usr/lib/python2.4/site-packages/FusionIcon
copying build/lib/FusionIcon/interface_qt4/__init__.py -> /usr/lib/python2.4/site-packages/FusionIcon/interface_qt4
copying build/lib/FusionIcon/interface_qt4/main.py -> /usr/lib/python2.4/site-packages/FusionIcon/interface_qt4
copying build/lib/FusionIcon/interface_gtk/__init__.py -> /usr/lib/python2.4/site-packages/FusionIcon/interface_gtk
copying build/lib/FusionIcon/interface_gtk/main.py -> /usr/lib/python2.4/site-packages/FusionIcon/interface_gtk
byte-compiling /usr/lib/python2.4/site-packages/FusionIcon/__init__.py to __init__.pyc
byte-compiling /usr/lib/python2.4/site-packages/FusionIcon/data.py to data.pyc
byte-compiling /usr/lib/python2.4/site-packages/FusionIcon/environment.py to environment.pyc
byte-compiling /usr/lib/python2.4/site-packages/FusionIcon/execute.py to execute.pyc
byte-compiling /usr/lib/python2.4/site-packages/FusionIcon/interface.py to interface.pyc
byte-compiling /usr/lib/python2.4/site-packages/FusionIcon/parser.py to parser.pyc
byte-compiling /usr/lib/python2.4/site-packages/FusionIcon/start.py to start.pyc
byte-compiling /usr/lib/python2.4/site-packages/FusionIcon/util.py to util.pyc
byte-compiling /usr/lib/python2.4/site-packages/FusionIcon/interface_qt4/__init__.py to __init__.pyc
byte-compiling /usr/lib/python2.4/site-packages/FusionIcon/interface_qt4/main.py to main.pyc
byte-compiling /usr/lib/python2.4/site-packages/FusionIcon/interface_gtk/__init__.py to __init__.pyc
byte-compiling /usr/lib/python2.4/site-packages/FusionIcon/interface_gtk/main.py to main.pyc
running install_scripts
copying build/scripts-2.4/fusion-icon -> /usr/bin
changing mode of /usr/bin/fusion-icon to 755
running install_data
copying images/22x22/fusion-icon.png -> /usr/share/icons/hicolor/22x22/apps
copying images/24x24/fusion-icon.png -> /usr/share/icons/hicolor/24x24/apps
copying images/48x48/fusion-icon.png -> /usr/share/icons/hicolor/48x48/apps
copying images/scalable/fusion-icon.svg -> /usr/share/icons/hicolor/scalable/apps
copying fusion-icon.desktop -> /usr/share/applications
Updating Gtk icon cache.
Cache file created successfully.

Then did Alt + F2 and put in fusion-icon, and hit run, still nothing.

---

### Post by zabien1970 on 2007-09-09
what happens when you press al+f2 and run ccsm?
It took me a month to figure out how to actually use this since there are hundreds of guides on how-to install but none on how to use.

---

### Post by AlexTepes on 2007-09-09
alex@alex-desktop:~$ ccsm
Info: No sexy-python package found, don't worry it's optional.
Traceback (most recent call last):
  File "/usr/local/bin/ccsm", line 37, in ?
    import compizconfig
ImportError: No module named compizconfig

Basically, I'm using XGL and  the fblah(Don't feel like opening xorg.conf to find it)
driver because of ATi, I have no idea how to get XGL running right away then get beryl to load, I figure its XGL *someting then beryl
Because I do:

alex@alex-desktop:~$ beryl --screen 0 --xgl-binding --xgl-rendering --force-xgl --replace
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Checking for non power of two texture support   : failed

Support for non power of two textures missing
beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: GLX_SGIX_fbconfig is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

x-server still goes on as AIGLX and I want XGL.

---

### Post by zabien1970 on 2007-09-14
Sorry for the delay in getting back.
  I see you were trying to install compiz but beryl is trying to run, you're probably best off removing all traces of beryl, compiz, and emerald and then start over.
  I used this link for mine [http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty)

---

