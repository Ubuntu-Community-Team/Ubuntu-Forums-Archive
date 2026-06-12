---
title: "add program to 'open with'-dialog"
date: 2014-12-31
forum: Desktop Environments
---

### Post by mito-o on 2014-12-31
hey there,

i'm using xubuntu 14.04 with the standard file browser. i installed mtPaint and found that there is no entry in the 'open with'-dialog.
i didn't want to make mtPaint to be my standard-program for opening images, i just wanted to add it to the list in the 'open with'-dialog.
so my question is: where can i find the file for adding the program?

i additionally have to say that i solved the original problem by first making mtPaint my favorite program to open images and then
changing back to the other program, but i still want to know where i can add programs 'by hand' - just for being a better unity with my system, you know? ;)

thanks for for your help

mito

---

### Post by schragge on 2014-12-31
The problem is the desktop file for mtPaint lacks MimeType information. Compare it e.g. with GIMP and Ristretto:
```
grep -s ^MimeType= /usr/share/applications/{gimp,ristretto}.desktop
```
I don't know for sure what image types mtPaint is able to handle, thus the MimeType line I add in the next workaround is pure guess. Tweak it accordingly.
```

mkdir -p ~/.local/share/applications
cp /usr/share/applications/mtpaint.desktop !$
echo 'MimeType=image/png;image/gif;image/jpeg;image/jpeg2000;image/bmp;image/tiff;image/x-xpixmap;image/x-xbitmap;image/x-targa;' >> !$
update-desktop-database !$:h

```
After that, mtPaint should show up in the *Open with...* list.

Don't forget to file a bug report against mtPaint for its lack of MimeType information. It's a universe package unchanged by Ubuntu, so better do it directly in [Debian BTS](https://bugs.debian.org/cgi-bin/pkgreport.cgi?src=mtpaint), not in Launchpad.

---

### Post by mc4man on 2014-12-31
If you decide to file a bug then wouldn't hurt to add that for Gnome it needs a %<letter> added to the Exec= line in the .desktop or it will never show up in a gnome3 based install 
Ex. - 
```
Exec=mtpaint %f
```

---

### Post by Dennis N on 2014-12-31
> i still want to know where i can add programs 'by hand'

I had the same situation: I wanted to have Shoutcast Playlists open with Geany from the "Open With.." dialog, but not set it as default.

Edited **~/.local/share/applications/mimeapps.list**

Added the section "Added Applications" (if may be already present) and my desired association (in red).

```
[Default Applications]
text/plain=mousepad.desktop

[COLOR="#FF0000"][Added Associations]
audio/x-scpls=geany.desktop; [/COLOR] 

```
Geany now appears on the "Open With..." dialog, but not as default.

Reference system: Xubuntu 14.10

---

### Post by mito-o on 2015-01-01
thanks for your help!

i will try out your advises and also send a bug-report with gnome information included.

mito

---

