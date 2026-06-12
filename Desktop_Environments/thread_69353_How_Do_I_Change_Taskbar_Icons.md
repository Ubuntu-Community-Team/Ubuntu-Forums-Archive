---
title: "How Do I Change Taskbar Icons?"
date: 2005-09-26
forum: Desktop Environments
---

### Post by palsyboy on 2005-09-26
Whenever I'm running Firefox, I have that stupid generic globe on the taskbar.  Whenever I'm using XMMS, I have that squared-off headphone icon on the taskbar.  I want to replace the globe with a nice Firefox icon, and I have a better icon I'd like to use for XMMS, too.  To clarify, I don't mean I want to change the launcher icons; I'm talking about the icon next to "XMMS - 7. Outkast - Knowing" and "Ubuntu Forums - Mozilla Firefox."

I've delved through /usr/share/icons, /usr/lib/mozilla-firefox/icons, and /usr/lib/xmms to find these icons to replace.  I tried replacing the four icons in /mozilla-firefox/icons, but I still get that globe.

Does anyone else know what to do?

---

### Post by greenstar on 2005-09-26
most of the icons will be found in:

*/usr/share/pixmaps* is full of icons

or

*usr/bin/subdir* - where /subdir=the folder of the app whose icon you're looking for, some of them - but not all - will be found in their own directory here.

as for firefox, here's the easy way: [http://www.ubuntuguide.org/#restoreoriginaliconsfirefox](http://www.ubuntuguide.org/#restoreoriginaliconsfirefox)

or just paste this into the console (taken from ubuntuguide):
```
wget -c http://frankandjacq.com/ubuntuguide/mozilla-firefox.png
wget -c http://frankandjacq.com/ubuntuguide/document.png
chmod 644 mozilla-firefox.png
chmod 644 document.png
sudo dpkg-divert --rename /usr/share/pixmaps/mozilla-firefox.png
sudo dpkg-divert --rename /usr/share/pixmaps/mozilla-firefox.xpm
sudo dpkg-divert --rename /usr/lib/mozilla-firefox/icons/default.xpm
sudo dpkg-divert --rename /usr/lib/mozilla-firefox/icons/document.png
sudo dpkg-divert --rename /usr/lib/mozilla-firefox/chrome/icons/default/default.xpm
sudo cp mozilla-firefox.png /usr/share/pixmaps/mozilla-firefox.png
sudo cp mozilla-firefox.png /usr/share/pixmaps/mozilla-firefox.xpm
sudo cp mozilla-firefox.png /usr/lib/mozilla-firefox/icons/default.xpm
sudo cp document.png /usr/lib/mozilla-firefox/icons/document.png
sudo cp mozilla-firefox.png /usr/lib/mozilla-firefox/chrome/icons/default/default.xpm
```

the Ubuntu guide has a wealth of tips, tricks and etc., give it a read.

---

### Post by palsyboy on 2005-09-26
Thanks!  That changed the Firefox icon successfully, but I can't find the XMMS icon anywhere, even when using slocate.  It seemed to be /usr/share/pixmaps/xmms_mini.xpm, but after replacing it and restarting XMMS, nothing happened.  There was no change even after I restarted KDE.  Hmm.

I'd used UbuntuGuide before but somehow missed that How-To.  I probably thought it was referring to changing the launcher icon or something.

---

### Post by greenstar on 2005-09-26
Glad I could help (My small way to give back to the community), and yes the ubuntuguide is excellent.

I have used smeg to customize icons, I just go find an image I want to use, make it the appropriate size - 32x32 pixels seems to be best but you can use 16 and maybe even 24 squared, and save as a .png file. drop that into /usr/share/pixmaps then use smeg to apply it as custom icon for XMMS or whatever else.

greenstar

**edit:**

After you change the icon with smeg, then run:
```
killall gnome-panel
``` 
this refreshes your gnome menu and your change should be visible after that.

---

### Post by palsyboy on 2005-09-27
I use KDE, not GNOME, so Smeg won't be useful for me.  Thanks, though.

---

