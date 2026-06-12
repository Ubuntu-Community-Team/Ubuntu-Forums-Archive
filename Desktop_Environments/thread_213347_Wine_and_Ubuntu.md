---
title: "Wine and Ubuntu"
date: 2006-07-11
forum: Desktop Environments
---

### Post by grav on 2006-07-11
Where the devil does Wine install itself?!!
I have apt-get'ed Wine, but I have no clue where Wine is now installed, and thereby no clue where Windows applications install themself.
If I run winecfg it says that my C: drive is located at "../drive_c" ... a relative path ... relative to what?!

Maybe this comes down to a general problem that I have - searching for files in Linux. I have tried the search function in Gnome, the "locate" and the "whereis" command, but none of them seem to work properly. They sometimes find something, sometimes they don't ... ](*,) ](*,) ](*,) ](*,)

---

### Post by Thund3rstruck on 2006-07-11
The wine directory structure is installed in ~/.wine

In other words: /home/YourUser/.wine

The "." period annotates it's a hidden folder. To expose hidden folders in Nautilus View > Show hidden files or in the console "ls -a"

---

### Post by mcman42 on 2006-07-11
I'll ask my question. Is it possible to install wine to some other folder other than home folder? Is it possible to move the wine folder to the other location without reinstalling wine?

---

### Post by dpm on 2006-07-12
Wine also creates a .desktop file for the programs it installs in the ~/gnome/Apps/Wine/Programs folder.

You can just drag and drop this file into Alacarte in order to create an entry in the GNOME menu for the installed win32 program, which is quite neat.

---

### Post by gymsmoke on 2006-07-12
I got wine installed.  How do you install windows apps with it?

---

### Post by vavoem on 2006-07-12
If finding stuff in linux is always your problem you should probably update your file catalog.
You can do so by running 

sudo updatedb

you'll bound to find things after that

---

### Post by philippe_carlo on 2006-07-12
> **grav said:**
>  ...
Maybe this comes down to a general problem that I have - searching for files in Linux. I have tried the search function in Gnome, the "locate" and the "whereis" command, but none of them seem to work properly. They sometimes find something, sometimes they don't ... ](*,) ](*,) ](*,) ](*,)

Before using locate, use updatedb (as root) to update the search index. Use find (see 'man find') for searching recursively through directory structures for files with certain properties (name/type/text). Whereis and which will only tell you where certain programs/binaries are installed - based on the PATH environment variables and other info.

---

### Post by dpm on 2006-07-12
> **gymsmoke said:**
> I got wine installed.  How do you install windows apps with it?

IIRC you run
```
winecfg
``` on the console to configure wine. You have to do this only once, although you can reconfigure wine later on if you wish.

To install programs with wine, you simply run the win32 installer for your program with wine, e.g.:
```
wine <your-programs-installer>.exe
``` but if I'm not mistaken, after wine is installed you can even simply click on the installer file in nautilus as if you were to open it, and it will be executed by wine, thus the installer will be run with wine.

---

### Post by qdvubun on 2006-07-12
yes you're right, you can double click the exe and wine will take over, its amazing. Same thing can be done in terminal.

---

