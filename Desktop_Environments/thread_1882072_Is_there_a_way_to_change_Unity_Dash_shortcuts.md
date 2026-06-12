---
title: "Is there a way to change Unity Dash shortcuts?"
date: 2011-11-16
forum: Desktop Environments
---

### Post by Stray Wolf on 2011-11-16
I have tons of photo's (45Gigs).  I've always preferred "digiKam" but I tried "Shotwell" since it came with 11.10.  I then purged it and installed digikam.  Now, when I select "View Photo's" from my Dash it opens the image viewer (I guess as a fall back since it can no longer find Shotwell).  Is there a way to set the Unity Dash "View Photo's" shortcut to open digikam?  Right now, Unity is so new it's hard to find any comprehensive guides that cover such things.

---

### Post by Copper Bezel on 2011-11-17
I'm not quite certain how the application is set for the "View Photos" button - it might be hard-coded, or it might follow your preferred app. If you double-click an image in the file manager, what does it load in?

You can change the default app for a mimetype by right-clicking it in the file manager, selecting Properties, and switching to the Open With tab. You could also try running System Info from the Dash and changing the Default Application setting there.

---

### Post by elliotn on 2011-11-17
yes change the open with in properties and unity will open it in that application

---

### Post by Stray Wolf on 2011-11-17
Thanks.  I went to System Settings>System Info>Default Applications.  The drop-down menu for photo's still gives Shotwell as an option even though it's not installed.  The only other options are Firefox and Image Viewer.  Oh well, I'll just keep a digikam icon on the launcher.  No big deal.

---

### Post by Copper Bezel on 2011-11-17
Yeah, it's really odd and a little annoying there's no option to add custom commands in System Info / Default Applications.

You could probably fix it, though; it just might be more work than it needs to be. in /usr/share/applications, there's a .desktop file for each application that the system uses to identify its path, but also its category and mimetypes. You might copy the one for digicam to ~/.local/share/applications (.local is a hidden directory in your home folder) and edit it to make sure it has the same category and mimetypes associated that Image Viewer does (drag and drop the file onto a gedit window to edit it):

```
Categories=GNOME;GTK;Graphics;RasterGraphics;Viewer;
```

and 

```
MimeType=image/bmp;image/gif;image/jpeg;image/jpg;image/pjpeg;image/png;image/tiff;image/x-bmp;image/x-gray;image/x-icb;image/x-ico;image/x-png;image/x-portable-anymap;image/x-portable-bitmap;image/x-portable-graymap;image/x-portable-pixmap;image/x-xbitmap;image/x-xpixmap;image/x-pcx;image/svg+xml;image/svg+xml-compressed;image/vnd.wap.wbmp;
```

Can't promise anything, but the new .desktop file will supersede the one in /usr/share/applications, and if you log out and log back in, digicam might appear in that list in Default Applications. And again, you might actually have to set this in the Nautilus "Open With" preferences for the mimetype, too.

---

