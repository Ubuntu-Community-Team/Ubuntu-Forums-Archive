---
title: "Old compiz config used instead of new compiz-fusion"
date: 2007-07-10
forum: Desktop Effects &amp; Customization
---

### Post by [h2o] on 2007-07-10
I followed the stucky guide to installing Compiz-fusion and when I run "compiz --replace" I get all the nice new shiny stuff working.
But, for some reason Compiz autostarts on login (never chose this, but maybe it is default?) and uses my old configurations (i.e using cube instead of wall, no ring-switcher, etc) and it is a bit annoying.

How do I completely remove all old configuration options?

---

### Post by dougfractal on 2007-07-10
to install the compiz config-settings-manager and run

```
sudo apt-get install compizconfig-settings-manager
ccsm
```

For  the Cube Atlantis and other extras
 
```
sudo apt-get install compiz-fusion-plugins-unofficial compiz-fusion-plugins-unsupported
```

from [Treviño&#8217;s Ubuntu Repository » feisty » eyecandy]("http://http://3v1n0.tuxfamily.org/dists/feisty/eyecandy/")

---

### Post by [h2o] on 2007-07-10
I have the ccsm application, and when I start it shows the settings I have chosen. These are the settings I get when I run "compiz --replace".

The problem is that there are other settings loaded when Gnome loads.

---

### Post by dougfractal on 2007-07-10
Purge the old compiz.

```
sudo apt-get purge compiz compiz-core
```

then follow the install guide at 
[http://www.compiz.org/Compiz_and_Copmiz_Fusion_GIT_Ubuntu_Repository](http://www.compiz.org/Compiz_and_Copmiz_Fusion_GIT_Ubuntu_Repository)
or any of the other guides available on the web. 

you could also try to remove the config file
```
rm -r ~/.compizconfig
```

---

### Post by [h2o] on 2007-07-13
I tried purging packages compiz and compiz-core and removing ~/.compizconfig, but it still loads old settings at login.

Ideas, anyone?

---

### Post by dougfractal on 2007-07-13
After all this, I think I have the same problem. I don't log out much so I didn't notice it.
Keep updating and I guess it will be fixed soon. 
 I guess it maybe that gnome hasn't loaded all the desktop settings. I tried running compiz --replace in the >system>preferences>sessions : order 80.  but I had 1 long composite desktop, not my settings. 

In the meantime, (for me anyway) ```
compiz --replace
``` reloads my settings

Make a desktop launcher and use that, to start compiz


```
echo "[Desktop Entry]
Encoding=UTF-8
Name=Compiz
GenericName=3D Window Manager
Comment=compiz daemon
Icon=/usr/share/compiz/icon.png
Exec=/usr/bin/compiz --replace
Terminal=false
Type=Application
Categories=GTK;GNOME;Application;Utility;
StartupNotify=true
X-Ubuntu-Gettext-Domain=compiz" > ~/Desktop/compiz.desktop
```

---

### Post by dougfractal on 2007-07-16
More on this topic visit:

[URL="http://forums.opencompositing.org/viewtopic.php?f=48&t=729&start=0&st=0&sk=t&sd=a#p5227"]
Compiz-Wrapper loader script [to run compiz and decos easily[/URL]

> 
Treviño quote:

Known Bugs

    * In few GNOME configurations, if you put compiz --replace on sessions, when gnome starts compiz is loaded only after some seconds (minutes) of freeze, while the gnome splash screen is shown... I can't understand why

> 
Jug quote:
That seems to be related to ubuntus native "desktop-effects". I noticed that if desktop-effects were enabled ubuntu loads compiz even if it's not in autostart. If trevinos wrapper-script is in the autostart at the same time there seems to be a conflict. Also in german ubuntu-forums It has been reported that this issue stopped when desktop-effects were installed, activated, deactivated and then uninstalled again.
Hope that helps anyone.

Didn't work for me.

---

### Post by [h2o] on 2007-07-16
Is there maybe a way to deactivate desktop-effects without having to install it? Using gconf-editor or something. Just need to know which key to look for.

---

