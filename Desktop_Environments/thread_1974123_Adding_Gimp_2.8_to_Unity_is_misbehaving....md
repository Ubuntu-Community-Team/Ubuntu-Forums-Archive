---
title: "Adding Gimp 2.8 to Unity is misbehaving..."
date: 2012-05-05
forum: Desktop Environments
---

### Post by ragtag on 2012-05-05
I installed Gimp 2.6.12 from the default repository, and then compiled gimp-2.8.0 to /opt/gimp/gimp-2.8.0 with a launcher that looks like this in /usr/local/bin/gimp-2.8

#!/bin/sh
export LD_LIBRARY_PATH=/opt/gimp/gimp-2.8.0/lib/
/opt/gimp/gimp-2.8.0/bin/gimp

So far so good. I can run it from the command line, and get an icon in Unity. Then I went into /usr/share/applications, and modified gimp.desktop to point to my new 2.8 version. I can now search for it with Dash, and start it from there. So far so good.

But, when I right click the Gimp icon and choose 'Lock to Launcher', then quite Gimp. It will not work from the launcher. Not only that. If I start it from the terminal, it will start just fine, but not show up in the launcher, nor in alt-tab.

I'm a bit stumped at this. Is there any way to fix this.

p.s. Gimp 2.6.12 works fine, if I leave gimp.desktop unchanged...but I would much rather use Gimp 2.8. :)

---

### Post by mc4man on 2012-05-05
When I built 2.8 here a month ago, (not currently on this new install) I didn't need to use a script to export & launch.

So in that case it was simple to create a .desktop _just for 2.8_ though you could use the script if need be on the Exec=, if so see note

Are you sure you need the launch script?
Anyway laid out basic here
[http://ubuntuforums.org/showpost.php?p=11818686&postcount=4](http://ubuntuforums.org/showpost.php?p=11818686&postcount=4)

For the .desktop I'll repeat here, though I used a slightly different Exec=, TryExec= red, then you show in your script
```
gedit ~/.local/share/applications/gimp2.desktop
```
```
[Desktop Entry]
Version=1.0
Type=Application
Name=Gimp 2.8
Comment=Create images and edit photographs
Exec=/opt/gimp-2.8/bin/[COLOR="Red"]gimp-2.8[/COLOR] [COLOR="Blue"]%U[/COLOR]
TryExec=/opt/gimp-2.8/bin/[COLOR="Red"]gimp-2.8[/COLOR]
Icon=gimp
Terminal=false
Categories=Graphics;2DGraphics;RasterGraphics;GTK;
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=GIMP
X-GNOME-Bugzilla-Component=General
X-GNOME-Bugzilla-Version=2.8.0
X-GNOME-Bugzilla-OtherBinaries=gimp-2.8
MimeType=application/postscript;application/pdf;image/bmp;image/g3fax;image/gif;image/x-fits;image/pcx;image/x-portable-anymap;image/x-portable-bitmap;image/x-portable-graymap;image/x-portable-pixmap;image/x-psd;image/x-sgi;image/x-tga;image/x-xbitmap;image/x-xwindowdump;image/x-xcf;image/x-compressed-xcf;image/x-gimp-gbr;image/x-gimp-pat;image/x-gimp-gih;image/tiff;image/jpeg;image/x-psp;image/png;image/x-icon;image/x-xpixmap;image/svg+xml;application/pdf;image/x-wmf;image/jp2;image/jpeg2000;image/jpx;image/x-xcursor;
```

Then just dragged it from ~/.local/share/applications/ on to the launcher, no issues
Edit:
 The Icon= presumes another package version of gimp installed, otherwise needs to be full-pathed to an icon

Just to note - even when I make a .desktop that uses an Exec=script I always end with a <space>%U or %F or %f. This will allow the .desktop to be seen in the r. click context menu, %U should be ok

---

### Post by ragtag on 2012-05-05
Thanks. That seems to have done the trick. You're right, I didn't need the shell script to launch it.

---

### Post by mc4man on 2012-05-05
i'm building it now - just noticed that there is a .desktop included in the source - gimp-2.8.0/desktop/ - basically what I posted though has the various other lang. comments & names

- -they should have come up with a new icon..

---

### Post by mips on 2012-05-06
> **mc4man said:**
> i'm building it now...

Why not use the PPA? Installed fine without any hassles for me.
```
sudo add-apt-repository ppa:otto-kesselgulasch/gimp
sudo apt-get update && sudo apt-get install gimp
```

---

### Post by ragtag on 2012-05-07
Does the ppa replace the original 2.6.12 version, or install alongside it? I want to be able to have access to both for now.

It's also nice to be able to compile your own versions if you want to test some of the bleeding edge stuff...like the integration of the MyPaint brush engine in gimp. :)

---

### Post by mc4man on 2012-05-07
The ppa installs to /usr as gimp & anyway upgrades gegl/babl to versions not likely to be compatible with a 2.6 repo package, so it's one or the other that way

---

