---
title: "[Solved] How to change an app icon..."
date: 2018-05-03
forum: Desktop Environments
---

### Post by paralis on 2018-05-03
... on dash to dock with 18.04?

Here is the situation:
I use the papirus icon theme with dash to dock. I don't like the new Corebird icon and I'd like to use the twitter icon for the Corebird application.

I changed the icon in /usr/share/applications/
The folder shows the new icon but dash to dock and arc menu don't. They don't give a damn.

Of course I could change the icon in /usr/share/icons/Papirus but I was trying to avoid that.

Anyway, suggestions appreciated.

Thank you

Eric

---

### Post by deadflowr on 2018-05-03
Did you change the icon for the thumbnail in /usr/share/applications
or did you change the name for the Icon in the corebird.desktop file itself?

You need to do the second one.
Easiest way is to copy the corebird.desktop file into your own home folder
(It has a special location for this at ~/.local/share/applications, short for /home/you/.local/share/applications, it's a hidden folder so you need to set it as unhide if using the file manager)
then use a text editor to open the desktop file and edit the Icon= line and change it to your icon and save it.

Depending on desktop version or icon used it or any number of random things might require a restart, or a log out  and login again, in order to show the new icon.

Also, if the icon isn't part of the default icon pack you are using, the Icon= needs the file path,
so if the icon was Icon=corebird and the new icon is a personal image, then you need to add it like
Icon=/path/to/icon/file/icon.ext

Hope it helps

---

### Post by paralis on 2018-05-03
Thank you for your quick answer.

I had changed the file (/usr/share/applications/corebird) icon but it didn't work. Investigating the content of the file (which name btw is oeg.baedert.corebird.desktop), I noticed two lines:

```
Icon[fr]=corebird
Icon=/usr/share/icons/Papirus/64x64/apps/twitter.svg

```

Changing the icon had also replaced the icon with complete path in the file but obviously it wasn't enough.
I replaced corebird with twitter on the first line, saved the file in ~/.local/share/applications/

and it worked right away without even leaving the session.

Solved!

Thank you, have a great day!

Eric

---

### Post by mörgæs on 2018-05-04
Thanks for an attempt at marking the thread solved but better to use Thread Tools.

---

