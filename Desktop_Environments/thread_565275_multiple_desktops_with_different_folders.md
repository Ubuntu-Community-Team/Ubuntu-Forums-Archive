---
title: "multiple desktops with different folders?"
date: 2007-10-02
forum: Desktop Environments
---

### Post by GIdervish on 2007-10-02
Hi,

I've been trying to reorganize my desktop to make it less cluttered, and the ideal way (for me) to do this would be to have a different set of files/folders present on different desktops, i.e. corresponding to different projects, etc.

The current folders are stored in ~/Desktop, so it seems like this would be a matter of adding another layer between the workspace layer and the desktop layer.

Does anyone know of a program that can do this?

Thanks

---

### Post by GIdervish on 2007-10-03
Ok, i've looked around a bit more, seen the same question asked quite a few times, without any success, and finally given up finding a program that already enables different icons on the different workspaces.

Now it's time to try a hack!

I'm using KDE, and after a bit of searching, found a global setting that will be useful to try and implement this :

in /home/$USER/.kde/share/config/kdeglobal
there is an option to set the desktop path:
e.g. Desktop=$HOME/Desktop

The plan is then to write a short script that can change this path when the workspace is changed.
While i'd love to have this occur when I change the workspace via the little windows on the bottom right of the screen, i'm not sure how to bind a script to such an action (any help here would be very welcome!), however it should be fairly easy to bind the script to a keyboard shortcut for changing workspace (e.g. CTRL-F2 to go to desktop 2, and run a script changing the desktop path).

Any suggestions for improvements to, or problems with this method?

---

### Post by GIdervish on 2007-10-04
Well, it seems as though multiple (real) desktops are possible, with a couple of workarounds.
(at least it works in KDE, and there's no reason why it shouldn't in gnome, etc. with a bit of adapting...)

Since i've noticed a lot of people asking this question in various threads, i'll post a possible way of doing it here - it works, although it's a bit messy at the moment.

The problem is basically to have multiple /home/$USER/Desktop folders, each containing different files/folders.
Can then have different desktops containing files/folders for different projects, etc.

One possible way to do this is by creating multiple desktop folders, and linking the /Desktop folder to whichever one is desired at the time.
Changing the desktop folder can then be done by killing the desktop (the process kdesktop in kde), deleting the link, creating a new link to the different folder, then restarting the desktop.

The workspace number (independent to the files/folders in the background) can also be changed.

A sample script for KDE (changing desktop folder to .desktop$1, and also changing the window) is:

killall -9 kdesktop
rm Desktop
ln -s .desktop$1 Desktop
kdesktop
dcop kwin KWinInterface setCurrentDesktop $1

Bind the script to some useful keys, e.g. Ctrl-F$1, and then it's working!

Unfortunately, this is still pretty messy, in that restarting kdesktop takes a couple of seconds. If anyone is still interested in implementing multiple (real) desktops, feel free to add some much needed improvements to this method.

---

