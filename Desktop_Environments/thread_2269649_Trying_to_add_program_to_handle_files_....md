---
title: "Trying to add program to handle files ... ?"
date: 2015-03-17
forum: Desktop Environments
---

### Post by kelt65 on 2015-03-17
I'd like to associate 'exfalso' and 'puddletag' to the list of apps which one can open with a right click in nautilus, but they are not in the list you get when you choose "Choose Program"  This used to let one type the path to any program you wanted, but now that is gone. How can one add one? I've removed ~/.config/mimeapps.list, but that evidently only works once ...

If I go to properties -> open with , I see a mistake I made at the top ("usr" shows up for when I typed "/usr/bin/exfalso" (and it works, but looks stupid), but I can't add anything or change anything from there. The buttons don't do anything. Most of the programs I'd like to open files with are never in the list of apps to choose from or "add".  How do I get them in there?

---

### Post by CantankRus on 2015-03-17
Usually adding a %U to the Exec line of the .desktop file in **/usr/share/applications** will allow
you to choose it in other applications.

eg I just installed exfalso then edited its desktop launcher in **/usr/share/applications**.
```
gksudo gedit /usr/share/applications/exfalso.desktop
```
and changed the line...
```
Exec=exfalso
```
to
```
Exec=exfalso [COLOR="#FF0000"]%U[/COLOR]
```
[ATTACH=CONFIG]260686[/ATTACH]
It's probably better practice to copy any desktop launchers from **/usr/share/applications** to **~/.local/share/applications**
and edit the copied file.

Once you have right clicked on a file and chosen exfalso to open it from the applications list an association is added to **~/.local/share/applications/mimeapps.list**
and it should now appear in the right click "open with" menu.
[ATTACH=CONFIG]260687[/ATTACH]


You could also manually add a mimetype association to **~/.local/share/applications/mimeapps.list**
to put it into the right click "open with" menu.
eg ```
gedit ~/.local/share/applications/mimeapps.list
```
and adding an mp3 association...
```
audio/mpeg=exfalso.desktop;
```

section of **~/.local/share/applications/mimeapps.list**
```
[Added Associations]
text/html=opera-developer.desktop;firefox.desktop;opera-browser.desktop;gedit.desktop;chromium-browser.desktop;google-chrome.desktop;midori.desktop;
text/xml=opera-developer.desktop;firefox.desktop;opera-browser.desktop;chromium-browser.desktop;google-chrome.desktop;
x-scheme-handler/https=opera-developer.desktop;firefox.desktop;opera-browser.desktop;chromium-browser.desktop;google-chrome.desktop;midori.desktop;
x-scheme-handler/ftp=opera-developer.desktop;firefox.desktop;opera-browser.desktop;google-chrome.desktop;
application/xhtml+xml=opera-browser.desktop;midori.desktop;
application/xml=firefox.desktop;gedit.desktop;opera-browser.desktop;
application/rss+xml=opera-browser.desktop;
application/rdf+xml=opera-browser.desktop;
image/gif=firefox.desktop;eog.desktop;
image/jpeg=firefox.desktop;eog.desktop;
image/png=firefox.desktop;eog.desktop;
video/webm=opera-browser.desktop;
application/x-deb=gdebi.desktop;
video/mp4=mplayer.desktop;
[COLOR="#FF0000"]audio/mpeg=exfalso.desktop;[/COLOR]
```

---

