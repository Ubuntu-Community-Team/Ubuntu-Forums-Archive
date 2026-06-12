---
title: "Where is the installed program?"
date: 2009-01-29
forum: General Help
---

### Post by Indyviews on 2009-01-29
I am using Ubuntu 8.10 and just installed ImageMagick with Synaptic. I don't see it in Applications and didn't find anything in the folders to start the programs. 

Is there some other way I am supposed to bring it up? I am hoping to open it and insert various photos.

---

### Post by Slim Odds on 2009-01-29
ImageMagick is a suite of command line programs.

display, convert, etc.

There is no GUI that I know of.

---

### Post by Indyviews on 2009-01-29
Thanks Slim, at least I know now that I am not blind.:)

---

### Post by geirha on 2009-01-29
You can find a list of files installed by a package by searching for the package at [http://packages.ubuntu.com](http://packages.ubuntu.com), by running the command ```
dpkg -L imagemagick
``` in a terminal, or in synaptic (right-click -> properties or something along those lines). 

If the package installs a .desktop-file under /usr/share/applications, it should show up in the menus. If not, it's likely a CLI app, with the executables usually installed in /usr/bin/

---

### Post by Slim Odds on 2009-01-29
> **geirha said:**
>  If not, it's likely a CLI app, with the executables usually installed in /usr/bin/

ImageMagick is numerous CLI apps: [http://www.imagemagick.org/script/index.php](http://www.imagemagick.org/script/index.php)

---

### Post by timcredible on 2009-01-29
imagemagick is used by other programs, like digikam, to create a slideshow with sound, etc.  it doesn't really do anything by itself, you could think of it as more of a library than anything else.

---

