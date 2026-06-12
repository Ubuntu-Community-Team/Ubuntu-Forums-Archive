---
title: "HOWTO Fix GIMP associating with PDF files (bare-hand approach)"
date: 2009-04-19
forum: General Help
---

### Post by amen51 on 2009-04-19
Th problem: after some updating (?), GIMP defaults to opening PDF files; this is especially annoying when firefox uses the same file association to open PDF's with GIMP.

I cannot trace the source of the problem. But, here is how I fixed mine; that is, made evince the default application. (Use at your own risk!)

-- System-wide setting
1- Locate ```
/usr/share/applications/defaults.list
``` which is usally  (hard?)-linked to /etc/gnome/defaults.list and make sure you have the line
```
application/pdf=evince.desktop
```

2-Locate ```
/usr/share/applications/mimeinfo.cache
``` and make sure you have the line ```
application/pdf=evince.desktop;
```
There could be other applications on the list, but evince should be the first.

3-Locate ```
/usr/share/applications/evince.desktop
``` and replace it with an uncorrupted version (see below).

-- Local setting 
1- Locate ```
~/.local/share/applications/mimeapps.list
``` and make sure you have something like
```
application/pdf=evince.desktop;
```
There could be other applications on the list, but evince should be the first.

2- Locate ```
~/.local/share/applications/evince.desktop
``` and delete it or replace it with an uncorrupted version (see below).


---
Here is a simple evince.desktop file you might want to use if yours is corrupted (which probably is if you are having this problem!)

```
[Desktop Entry]
Name=Document Viewer
TryExec=evince
Exec=evince %U
StartupNotify=true
Terminal=false
Type=Application
Icon=evince
NoDisplay=true
X-GNOME-DocPath=
X-GNOME-Bugzilla-Bugzilla=GNOME
X-GNOME-Bugzilla-Product=evince
X-GNOME-Bugzilla-Component=general
X-GNOME-Bugzilla-Version=2.22.2
Categories=GNOME;GTK;Graphics;VectorGraphics;Viewer;
MimeType=application/pdf;application/x-bzpdf;application/x-gzpdf;application/postscript;application/x-bzpostscript;application/x-gzpostscript;image/x-eps;image/x-bzeps;image/x-gzeps;application/x-dvi;application/x-bzdvi;application/x-gzdvi;image/vnd.djvu;image/tiff;application/x-cbr;application/x-cbz;image/*;application/vnd.sun.xml.impress;application/vnd.oasis.opendocument.presentation;
X-Ubuntu-Gettext-Domain=evince
```

You may want to also look here which inspired this post: 
[http://forums.fedoraforum.org/archive/index.php/t-26875.html]("http://forums.fedoraforum.org/archive/index.php/t-26875.html")
Good luck!

---

### Post by cinematography on 2009-04-19
To change the file association the easy way :D right click the file (in this case, any pdf file) go to properties, go to the "open with" tab, and select the program you'd like the pdf files to be opened with. That's how I do it, and it works fine.

---

### Post by Rallg on 2009-04-19
Ah, but the problem had to do with Firefox. In my case, "Always Ask" failed to work after recent updates (it tried to use adobe Reader 8, but I have 9). Within Firefox, I fixed it by manually choosing Evince. For a downloaded file, the right-click properties worked. The original post is probably the most complete solution.

---

### Post by amen51 on 2009-04-20
cinematography, yes that is the easy way, but sometimes it won't work, for example when  evince.desktop is corrupted or for some reason your system-wide and local settings are different. (Right-click doesn't seem to fix everything!)

---

