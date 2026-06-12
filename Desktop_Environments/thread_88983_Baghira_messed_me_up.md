---
title: "Baghira messed me up"
date: 2005-11-11
forum: Desktop Environments
---

### Post by vh1 on 2005-11-11
so about a half hour ago I figured I'd install baghira to see what it's all about

I only did a normal `sudo apt-get install kwin-baghira`, didn't want to bother with sources. applied it, used it for about ten minutes, realized I didn't really like it, removed it with `dpkg -P kwin-baghira`

now, every time I login to KDE my top menu bar is way oversized, and it complains about some baghiramenu applet that it can't load. and I can't find where to remove it

also, I don't know how, why or if baghira is the cause of this, but for some reason whenever I load .php files from an FTP site in remote:/, it loads the temp file even though the command used to open it is `kwrite **%U**`. it didn't do this before

---

### Post by aysiu on 2005-11-11
If you used ```
sudo apt-get install kwin-baghira
``` to install Baghira, I'm confused as to why you used ```
dpkg -P kwin-baghira
``` to uninstall it. I don't even know what -P means. The best way to uninstall it would have been ```
sudo apt-get remove baghira
```.

Also, when you don't like a theme, you can just switch to another one. You don't have to uninstall the theme (unless, for some reason, you think it takes up too much hard drive space...?).

I'd do a search for files containing the word *baghira* and see what pops up. Likely, there's some config file that wants to start the baghira applet, and you can just modify that config file (back up the file before modifying it, though).

---

### Post by vh1 on 2005-11-11
[QUOTE=aysiu]If you used ```
sudo apt-get install kwin-baghira
``` to install Baghira, I'm confused as to why you used ```
dpkg -P kwin-baghira
``` to uninstall it. I don't even know what -P means. The best way to uninstall it would have been ```
sudo apt-get remove baghira
```.

Also, when you don't like a theme, you can just switch to another one. You don't have to uninstall the theme (unless, for some reason, you think it takes up too much hard drive space...?).

I'd do a search for files containing the word *baghira* and see what pops up. Likely, there's some config file that wants to start the baghira applet, and you can just modify that config file (back up the file before modifying it, though).[/QUOTE]

`dpkg -P *package*` removes the package and all configuration files. after I used baghira I realized there's little chance of me wanting to use it again so there was no harm in purging the config files as well. it's not that I think the package took up too much space, it's that I don't like having things installed that I don't use.

your searching for files containt baghira was a great suggestion though! I think I found what I was looking for

---

### Post by aysiu on 2005-11-11
[QUOTE=vh1]
your searching for files containt baghira was a great suggestion though! I think I found what I was looking for[/QUOTE] I hope it works out for you.

---

