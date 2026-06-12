---
title: "Google Earth Icon (only) is missing"
date: 2011-02-08
forum: Desktop Environments
---

### Post by RogerDavis on 2011-02-08
I used the "Googleearth Package - utility to automatically build a Debian package of Google Earth" to install Google Earth. Everything was fine for a long time, but recently the desktop icon is a blank sheet of paper. Google Earth works, just the icon is goofy.

From the Google-googleearth.desktop file, I see an icon is supposed to be connected with file googleearth-icon.png , but I can't find this file anywhere.

How do I fix the icon?

---

### Post by ankspo71 on 2011-02-08
Hi,
I don't think it is necessary to create a deb file for Google Earth anymore, since the Google Earth homepage is offering deb file downloads now. I'm using Google Earth 6 which I got from the Google Earth Homepage (32bit deb). (Their download requires lsb-core to be installed in order for it to work)

Anyways, to get the icon on your desktop working, try setting the icon location in the *.desktop file as "Icon=google-earth" like shown below. 

---

The files '/usr/share/applications/google-earth.desktop' and '/opt/google/earth/free/google-earth.desktop' both say this:

[Desktop Entry]
Version=1.0
Name=Google Earth
GenericName=3D planet viewer
Comment=Explore, search and discover the planet
Exec=/opt/google/earth/free/google-earth %f
Terminal=false
MultipleArgs=false
**Icon=google-earth**
Type=Application
Categories=Application;Network
MimeType=application/vnd.google-earth.kml+xml;application/vnd.google-earth.kmz;application/earthviewer;application/keyhole

---

The icons Google Earth provided (I think) are located here:

/usr/share/icons/hicolor/128x128/apps/google-earth.png
/usr/share/icons/hicolor/16x16/apps/google-earth.png
/usr/share/icons/hicolor/22x22/apps/google-earth.png
/usr/share/icons/hicolor/24x24/apps/google-earth.png
/usr/share/icons/hicolor/256x256/apps/google-earth.png
/usr/share/icons/hicolor/32x32/apps/google-earth.png
/usr/share/icons/hicolor/48x48/apps/google-earth.png
/usr/share/icons/hicolor/64x64/apps/google-earth.png

Hope this helps.

---

### Post by okkie on 2011-02-09
Thanks for the info but I cannot install lsb-core.It goes halfway and then says packages are missing.Is there a place where a working version can be downloaded please ?

---

