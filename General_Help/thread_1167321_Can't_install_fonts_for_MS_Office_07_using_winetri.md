---
title: "Can't install fonts for MS Office 07 using winetricks"
date: 2009-05-22
forum: General Help
---

### Post by miocene on 2009-05-22
I've successfully installed MS Office 2007 which runs great under WINE. Only problem being I can't install the core fonts needed by it. A really basic font is displayed in their place.

I ran:
```
harry@harry-desktop:~$ sh winetricks corefonts tahoma vcrun2005sp1 wsh56js
```

to install the fonts. And I got back:
```

Executing wget -nd -c --read-timeout=300 --retry-connrefused --header Accept-Encoding: gzip,deflate http://downloads.sourceforge.net/corefonts/arial32.exe
--2009-05-22 23:23:15--  http://downloads.sourceforge.net/corefonts/arial32.exe
Resolving downloads.sourceforge.net... 216.34.181.59
Connecting to downloads.sourceforge.net|216.34.181.59|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: http://kent.dl.sourceforge.net/sourceforge/corefonts/arial32.exe [following]
--2009-05-22 23:23:16--  http://kent.dl.sourceforge.net/sourceforge/corefonts/arial32.exe
Resolving kent.dl.sourceforge.net... 212.219.56.167
Connecting to kent.dl.sourceforge.net|212.219.56.167|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 554208 (541K) [application/octet-stream]
arial32.exe: Permission denied

Cannot write to `arial32.exe' (Permission denied).
Note: command 'wget -nd -c --read-timeout=300 --retry-connrefused --header Accept-Encoding: gzip,deflate http://downloads.sourceforge.net/corefonts/arial32.exe' returned status 1.  Aborting.
```

My question is why didn't it work and how can I get it to work?

---

### Post by miocene on 2009-05-23
Anyone know how I can sort this??

---

### Post by Legace on 2009-05-23
Make sure you've got the core fonts installed. (Check that **ttf-mscorefonts-installer** is installed in Synaptic)

Then open the following folder:
/usr/share/fonts/truetype/msttcorefonts


and copy the fonts to:
```
~/.wine/drive_c/windows/Fonts
```

---

### Post by miocene on 2009-05-25
I think that worked. Although the fonts (especially calibri) look slightly different. But maybe that's to do with the font smoothing in WINE.
Cheers

---

