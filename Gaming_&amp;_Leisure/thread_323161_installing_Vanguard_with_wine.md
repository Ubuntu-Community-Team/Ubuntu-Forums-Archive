---
title: "installing Vanguard with wine"
date: 2006-12-21
forum: Gaming &amp; Leisure
---

### Post by dasuberdog on 2006-12-21
So I am having problems installing things with wine.  I use Promash and when I go to install it the installer shield works fine and says its finished installing but it seems like nothing gets installed.  Or atleast I don't know where it is getting installed because when I restart install shield it says its already installed.

Anyway I am having the same problem with Vanguard Beta installation.

Anyone know what I'm doing wrong or where the programs would be installed?

---

### Post by hikaricore on 2006-12-21
Most often if you choose the default install directory, programs are installed in:

*~/.wine/drive_c/Program\ Files/*

which is the same as:

*/home/YOURUSERNAME/.wine/drive_c/Program\ Files/*

The \ is needed before spaces in directory or file names in linux unless you put the entire thing in quotes example:

***"**~/.wine/drive_c/Program Files/**"***

Also files names and folders names are _CaSe SeNsItIvE_ :P hehe

Hope this helps a little bit.

--Aaron

---

### Post by dasuberdog on 2006-12-21
Yes thanks.  I figured out that the wine folder is hidden.  I still think in windows even though I'll never go back.

---

