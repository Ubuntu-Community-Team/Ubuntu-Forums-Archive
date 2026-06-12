---
title: "Trouble with Icons"
date: 2009-06-14
forum: General Help
---

### Post by moldy on 2009-06-14
Hi all

I am trying to install a new icon theme, just for something different.  Namely this one:  [http://art.gnome.org/download/themes/icon/1008/ICON-Kreski-Lines.tar.gz](http://art.gnome.org/download/themes/icon/1008/ICON-Kreski-Lines.tar.gz)

I've installed it, but it seems that only ".doc" files have been given the new icons.

Any clue why the rest of the icons might not be working?

Richard.

---

### Post by moldy on 2009-06-15
bump::

---

### Post by CatKiller on 2009-06-15
There should be new icons for every MIME type that has an icon in the 64x64/mimetypes directory. I don't know why they aren't showing up on your install.

---

### Post by moldy on 2009-06-15
> **CatKiller said:**
> There should be new icons for every MIME type that has an icon in the 64x64/mimetypes directory. I don't know why they aren't showing up on your install.

Hey CatKiller - sorry, I wasn't clear.  In the ./icons/Kreski-Lines/64x64 directory there is the full range of icons.  The problem is, when I apply the icon theme, only the .doc ones actually work!

---

### Post by t4ggs on 2009-06-15
try going to /home/user/.icons and open an already installed icon theme that is working and see if the structure of folders is the same as this theme u r trying to install

---

### Post by CatKiller on 2009-06-15
I've just applied the theme on my install, and I get new icons for a whole bunch of other filetypes; zip files, html and ISO all show up using the new theme. (btw, uncommenting the Inherits line in the index.theme file makes it look less hideous. You need to drag&drop the file onto a text editor to edit it.)

Perhaps there's something wrong with your MIME Type database? Do other icon themes apply the correct icons for the other file types? What other file types are they that aren't changing with the new icon theme? What size are the icons that you're looking at?

---

### Post by moldy on 2009-06-20
> **CatKiller said:**
> I've just applied the theme on my install, and I get new icons for a whole bunch of other filetypes; zip files, html and ISO all show up using the new theme. (btw, uncommenting the Inherits line in the index.theme file makes it look less hideous. You need to drag&drop the file onto a text editor to edit it.)

Perhaps there's something wrong with your MIME Type database? Do other icon themes apply the correct icons for the other file types? What other file types are they that aren't changing with the new icon theme? What size are the icons that you're looking at?

Yeah, other icon themes seem to apply properly.  Examples of icons not installing are the folder icon, HDD icon etc.  Some of the file types are working but not most.  bizarre.

---

### Post by CatKiller on 2009-06-20
I've removed the theme now, but I definitely got the folder icons changing. I'm out of ideas for why its not working for you.

Are you really still on Gutsy? I know that with one of the changes to Gnome, some of the names for which icon represented what changed. I remember that the Trash icon name changed, so some themes didn't have an icon for that. Perhaps something similar is happening here. You could go through a theme that does work and for the icons that are named differently, make a symlink in this theme that is called what the working theme calls that icon.

---

