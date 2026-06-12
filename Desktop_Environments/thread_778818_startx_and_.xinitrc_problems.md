---
title: "startx and .xinitrc problems"
date: 2008-05-02
forum: Desktop Environments
---

### Post by firmit on 2008-05-02
I have a problem. It might be some kind of setting I have not done yet, so any help will be highly appreciated.

I installed xubuntu 8.04 alt. commandline (CLI) only. 
Then I issued after updating the corresponding sources.list 
```
$ sudo apt-get install xorg lxde dbus hal obconf
```

My plan is to try out LXDE as DE which uses openbox as WM. Yes, I have made a post here: 
[http://ubuntuforums.org/showpost.php?p=4860848&postcount=59](http://ubuntuforums.org/showpost.php?p=4860848&postcount=59)
but hopefully for a bigger audience I made a semi-duplicate here.

If anyone could take a look, I'd really appreciate it. I think the problem boils down to permissions, or something related.

On lxde.sourceforge.net, it states that if I do NOT have a display manager installed, I should create .xinitrc with startlxde: 
```
$ echo startlxde > ~/.xinitrc
```
(exec startlxde gives same problem)
Now I issued
```
startx
```
LXDE starts.

Now my problems. 
1) automount does not work
2) Theme's do not work proberly. lxapperance, once installed, do not change the window behavior (title bar, border etc), only icons and theme inside of windows. Obconf works and saves.
3) .Xresources is NOT loaded / used - I have configured xterm here.

Okei - so I delete the .xinitrc file. And $ startx with new sets of problems (and fix!):

LXDE starts.
1) automount works!
2) I am not able to edit and save with obconf (~/.config/openbox/lxde-rc.xml) to my liking, not manually either. With obconf I get error while saving. 
3) .Xresources is loaded
4) Alt-F2 keybinding for the RUN dialog (lxpanelctl run) is not working anymore...
5) I may shutdown, restart from lxde-logout

Regarding automount: I am member of 'plugdev'. PCManfm works as volume manager.
](*,)
What am I doing wrong?

---

### Post by firmit on 2008-05-04
Never mind - I gave up.

Sorry all - but I "converted" to Debian Lenny, using LXDE as DE and Openbox as WM. Working perfectly. Ram usage down to 39.98 MB ram after startup!

[http://firmit.wordpress.com/2008/05/04/lxde-installation-first-successful-run/](http://firmit.wordpress.com/2008/05/04/lxde-installation-first-successful-run/)

---

