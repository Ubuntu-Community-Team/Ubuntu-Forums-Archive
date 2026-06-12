---
title: "Close, maximize, &amp; minimize buttons on the panel"
date: 2009-02-28
forum: General Help
---

### Post by Greg T. on 2009-02-28
Attached are three scripts that, when added to a panel with launchers, can be used in place of the close, maximize, and minimize buttons of the active window. I use these on my top panel with the close button in the upper right-hand corner of the screen. 

Why do this? Two reasons. First, as Fitts' Law indicates, this approach decreases the amount of time it takes to hit these buttons; instead of carefully aiming at a little button on a window, I can throw my mouse to reach the buttons. Given the frequency with which I use the close button in particular, this is a good thing.

Second, for netbook owners and others interested in maximizing screen space, this approach effectively eliminates the need for a title bar when a window is maximized. How to eliminate the title bar for maximized windows in Compiz is explained below.

There is a little hidden functionality in the scripts. For instance, the close script will switch to other viewports/desktops when there are no windows left to close in the current viewport/desktop. It also will invoke Gnome's shutdown dialog if there are no windows left to close. If you want a full rundown, check out the comments in each script, which are comprehensive. (Among other things, it includes alternative commands to invoke the KDE shutdown if you're running Kubuntu.)

**Prerequisites**

The scripts were written for Ubuntu 8.10 (Gnome). If you're running an earlier version or KDE or XFCE, you will need to tweak the "close.py" script before using it. The instructions for doing so are in the script; just open it with a text editor and follow the instructions.

There are some dependencies that need to be met. The scripts are dependent upon some Gnome-specific libraries. If you're not using Gnome, it may pull in a large number of packages (30+ packages, 50+ MB on a fresh install). Just a fair warning. To install the dependencies, type the following in a terminal:

```
sudo apt-get install python-gnome2-extras wmctrl xwit[ python-wnck
```

**Setup**

Download the scripts attached below, as well as the images in the following post. (I attached them in separate posts due to the forum limit of five attachments per post.)

Make the scripts executable. *Make sure to do this! Failure to set permissions is the most likely cause if the scripts don't work for you.* If you have saved them to your home directory, type in a terminal:

```
chmod 755 close.py
chmod 755 maximize.py
chmod 755 minimize.py
```

Now, create launchers for these on the panel. For instance, to add the close button to the panel, right click on the panel, select "Add to Panel..." and in the box that follows select "Custom Application Launcher" at the top of the list. Another box appears: Enter "Close" in the Name field and the directory of the script in the Command field, then click on the "spring" icon to select the directory of the close button image you downloaded. 

Do the same for the other two launchers and you should be good to go. Give it a try and enjoy (hopefully).

If you want to eliminate the title bar of maximized windows in Compiz, you should use ccsm, the Compiz settings manager. If you don't have it, add it as follows:

```
sudo apt-get install compizconfig-settings-manager
```

Then start ccsm:

```
ccsm
```

Click on Window Decorations, and in the field for "Decoration windows" replace the default "any" with "!state=maxvert".

---

### Post by Greg T. on 2009-02-28
Attached are the images that can go with the scripts.

---

### Post by Repgahroll on 2009-08-14
Thank you very much master! :)

Used togetha with maximus (disabling auto maximization thru gconf-editor) it's pure fun!

Anyway... there shoulda be a way to hide the buttons if the window isnt maximized i think the easiest way is to simply change the icon to a "transparent" one.

```
Screenshots coming soon!
``` :D

Thank you man! :)


[B][SIZE=4]SCREENSHOTS:

WINDOWED APPLICATIONS:[/SIZE]
[/B][IMG]http://ubuntuforums.org/attachment.php?attachmentid=124915&stc=1&d=1250296650[/IMG]


[SIZE=4]**FULLSCREEN APPLICATION (NO WINDOW BAR :) ) NOTICE THE WINDOW BUTTONS ON TOP RIGHT CORNER**[/SIZE]
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=124916&stc=1&d=1250296650[/IMG]

---

### Post by unimatrix on 2009-11-03
I think you should try Window Applets:
[http://www.gnome-look.org/content/show.php/?content=103732](http://www.gnome-look.org/content/show.php/?content=103732)

---

