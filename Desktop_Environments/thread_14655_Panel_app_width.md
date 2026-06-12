---
title: "Panel app width?"
date: 2005-02-08
forum: Desktop Environments
---

### Post by Saibei on 2005-02-08
Howdy all,

upgraded to hoary and now all of my applications take up the same 10% of the panel (see attached image). I have to set the minimum size to like 400 to get a decent size, and that can't be right. 

I suspect the culprit is one package I can't get to install right via the gui updater or sudo apt-get upgrade. Error is: ```
Unpacking replacement gnome-icon-theme ...
dpkg: error processing /var/cache/apt/archives/gnome-icon-theme_2.9.91-0ubuntu2_all.deb (--unpack):
 trying to overwrite `/usr/share/icons/hicolor/48x48/apps/gnome-run.png', which is also in package gnome-panel-data
dpkg-deb: subprocess paste killed by signal (Broken pipe)
```

---

### Post by rosslaird on 2005-02-09
Try logging out, logging back in to the "Gnome failsafe terminal", and running apt-get from there (i.e. outside of Gnome). It worked for me -- I had the same problem.
You might try:

sudo apt-get -f install

Or just:

sudo apt-get upgrade

---

### Post by lao_V on 2005-02-09
Ever since I installed Ubuntu on my PC, all my windows on the panel were of that size.

---

### Post by Saibei on 2005-02-10
[QUOTE=lao_V]Ever since I installed Ubuntu on my PC, all my windows on the panel were of that size.[/QUOTE]
 No more info on this? No clue how to fix it? I got the package (hoary repository problem was to blame) but their still so small :(

---

### Post by Greg T. on 2005-02-10
This is a known bug, I believe. I saw some sort of Ubuntu buzilla entry on it tonight, but don't recall the number.

For me, the temporary workaround is to set the minimum width to 1024. To do so, right click on the grippy on the far left of the windows list, click on preferences, and click on the size tab to enter the new size. Setting maximum width doesn't seem to do anything.

---

