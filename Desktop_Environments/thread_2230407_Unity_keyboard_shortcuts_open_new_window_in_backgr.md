---
title: "Unity: keyboard shortcuts open new window in background"
date: 2014-06-19
forum: Desktop Environments
---

### Post by random_jc on 2014-06-19
Hi everybody,

When opening an application through a keyboard shortcut I defined (of  the sort Ctrl+Alt+[some letter]), it often happens that the application  is opened in a window that is kept in the background. The phenomenon  happens every time with certain shortcuts (those pointing to  thunderbird or firefox), never with others (custom shortcut for gnome-terminal in a  specific folder), and "depends" with yet others (it seems that a  shortcut to Gedit will pop up nicely in the foreground if gedit is  closed, but otherwise will open a new document and keep the gedit window  in the background ; that a shortcut to nautilus in a specific  folder will open an "active" window if no other window was open, but will otherwise open a window in the background).

The phenomenon happens on two fresh installs of Ubuntu 14.04 LTS (a laptop and a desktop computers). It  basically kills all the interest of defining efficient keyboard  shortcuts. Does anyone know how to fix this?

Thanks.

---

### Post by rc-artworx on 2014-10-10
I have the same problem.
Either I use the calculator button on my keyboard or any other shortcut, the application opens behind all other opened windows, forcing me to switch to it.
Since I have two displays, my workaround is to position my mouse on the other display an presse the shortcut, but I have to click the application to push it forward.
It's quite annoying and defeats the purpose of using shortcuts.

---

### Post by laszlo-krekacs-list on 2014-10-15
$ccsm

Settings Manager > General > General Options > Focus and Raise Behaviour > Focus Prevention Level > OFF

For more details, please refer to:
[http://askubuntu.com/questions/165908/unity-nautilus-folder-opens-in-background](http://askubuntu.com/questions/165908/unity-nautilus-folder-opens-in-background)

---

### Post by rc-artworx on 2014-10-16
Excelent!!! It worked like a charm!!
And since I was there, I also disabled the "click to focus".
I used to love the focus on mouse over and now I have it back!
I didn't knew these options since I've never used them since Ubuntu 5.04
Thank you very much!

---

