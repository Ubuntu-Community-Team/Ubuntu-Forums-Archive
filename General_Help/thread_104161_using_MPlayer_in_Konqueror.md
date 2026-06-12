---
title: "using MPlayer in Konqueror"
date: 2005-12-15
forum: General Help
---

### Post by mtc on 2005-12-15
I'm using Fluxbox as my WM, however I would like to use Konqueror as a browser, without the rest of KDE, like kicker or kdesktop. I've installed the 3.5 version and it works, however I can't make it play movies. I have the MPlayer Mozilla plugin installed and it is associated with movie files, but when I try to open any file, I get the message "Unable to load Netscape plugin for [url]".
When that happens, Konqueror writes to the console "nspluginviewer (plugin): ERROR: Can't create plugin class".
When I browse local fs, right click on the file and select "Open with MPlayer" nothing happens.
MPlayer works when I run it alone, and as a plugin in Firefox.
Does anyone know what is the reason and how can it be fixed?

---

### Post by mtc on 2005-12-15
Sorry to create multiple posts, I've just noticed, that when I set the option "run in terminal" for MPlayer, the right click->open with MPlayer method works, however playing videos inside Konqueror is still impossible.

---

### Post by limit223 on 2005-12-15
For sure you missed to install a package which get konqueror open that file with gmplayer.. 

Just curios what's the output of the command:

konqueror --mimetype video/.avi name_of_avi_here.avi

or other extension that you want to play with gmplayer?

---

### Post by mtc on 2005-12-15
And which package would it be?

If the "run in terminal" option is checked for MPlayer, the command opens Konqueror and then shows that file in MPlayer, if the option is unchecked, an empty Konqueror window shows.
On the console it shows warnings "servicetype video/.avi not found", if I write "video/avi" i get the same "unable to load netscape plugin" error as before.

---

### Post by ltmon on 2005-12-15
Do a search on these forums for "kmplayer".  You will have to compile yourself, but there are pretty thorough instructions on doing this.

Once that is done you can easily change the default file associations for all your video mimetypes in the "Configure Konqueror..." dialog.

L.

---

