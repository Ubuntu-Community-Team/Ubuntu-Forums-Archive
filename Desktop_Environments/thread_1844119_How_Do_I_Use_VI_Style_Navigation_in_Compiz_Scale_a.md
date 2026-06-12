---
title: "How Do I Use VI Style Navigation in Compiz Scale and Move Modes?"
date: 2011-09-14
forum: Desktop Environments
---

### Post by CH3CH2OH on 2011-09-14
Is it possible to use vi style navigation (hjkl) in lieu of the arrow keys in Compiz Scale Mode? This feature appears to have been implemented over a year ago: 
[http://https://launchpad.net/~tualatrix/+archive/personal/+sourcepub/1283754/+listing-archive-extra]("http://https//launchpad.net/%7Etualatrix/+archive/personal/+sourcepub/1283754/+listing-archive-extra")

However, there does not seem to be support for it in my Compiz build on Natty (Compiz 0.9.4.0). Furthermore, the current source code in the repos does not contain the extra keycodes from the diff:
+-    sd->leftKeyCode  = XKeysymToKeycode (d->display, XStringToKeysym ("Left")); +-    sd->rightKeyCode = XKeysymToKeycode (d->display, XStringToKeysym ("Right")); +-    sd->upKeyCode    = XKeysymToKeycode (d->display, XStringToKeysym ("Up")); +-    sd->downKeyCode  = XKeysymToKeycode (d->display, XStringToKeysym ("Down")); ++    sd->leftKeyCode  = XKeysymToKeycode (d->display, XStringToKeysym ("h")); ++    sd->rightKeyCode = XKeysymToKeycode (d->display, XStringToKeysym ("l")); ++    sd->upKeyCode    = XKeysymToKeycode (d->display, XStringToKeysym ("k")); ++    sd->downKeyCode  = XKeysymToKeycode (d->display, XStringToKeysym ("j"));

I'm going to try adding them in the source and compiling my own version of Compiz, but there should be support for this built in to the repository's binary. :-/



#####EDIT#####
I solved the problem by editing the source code for the scale plugin and compiling a new shared library (libscale.so).  Instructions for compiling are as follows:

$ cd  ### makes sure you are in your home directory -- it is simpler that way
$ sudo apt-get build-dep compiz  ### make sure you have everything you need to compile this
$ sudo apt-get source compiz  ### get the source code
$ cd compiz_0.9.4+bzr20110606/plugins/scale/src    ###depending on when you do this, your version number may differ here
$ sudo mv scale.cpp backup_scale.cpp  ###backup the source code
$ sudo cat backup_scale.cpp | sed s/'    downKeyCode  = XKeysymToKeycode (screen->dpy (), XStringToKeysym ("Down"));'/'    downKeyCode  = XKeysymToKeycode (screen->dpy (), XStringToKeysym ("Down"));\n    leftKeyCode  = XKeysymToKeycode (screen->dpy (), XStringToKeysym ("h"));\n    rightKeyCode = XKeysymToKeycode (screen->dpy (), XStringToKeysym ("l"));\n    upKeyCode    = XKeysymToKeycode (screen->dpy (), XStringToKeysym ("k"));\n    downKeyCode  = XKeysymToKeycode (screen->dpy (), XStringToKeysym ("j"));'/ > scale.cpp  ###make a modified source file

Now that you have made the new source file, I highly recommend you drop to the command line and shut down your graphical interface for the next part. WARNING: this will blast any windows you have  open. Make sure to shut everything down first and save changes.  Also, you'll need to  print this out or have another computer handy before you do this.  I'm  not certain that it is totally necessary, but it is a reasonably good idea to not be in the GUI while you're modifying it. To do this:
hit ctrl+alt+F1 and login with your username and password. Then you run:
$ sudo stop gdm  ### this shutdowns gnome and all the graphical interface
$ cd compiz_0.9.4+bzr20110606/plugins/scale/src    ###depending on when you do this, your version number may differ here
$ mkdir build ### make the build dir
$ cd build ### move into the build dir
$ sudo cmake ..  ### configure the compilation
$ sudo make  ### compile the source code
$ sudo mv /usr/lib/compiz/libscale.so /usr/lib/compiz/backup_libscale.so  ### backup the old libscale.so
$ sudo cp plugins/scale/libscale.so /usr/lib/compiz/ ### drop the new libscale.so  into place
$ cd  ### get back to your home dir
$ sudo rm -rf compiz_0.9.4+bzr20110606 ###cleanup the unused directory
$ sudo shutdown -r now ### restart your machine technically, you shouldn't need to do this, but i found gdm wouldn't start properly until i did  :-/


Good luck with this! Hope this helps someone else who was frustrated by the lack of this feature. 

Obviously, this fix is for scale.  It is the same process with the other source file if you want to add hjkl support move.

---

### Post by danilkutkevich on 2011-11-12
> **CH3CH2OH said:**
> I solved the problem by editing the source code for the scale plugin and compiling a new shared library (libscale.so).  Instructions for compiling are as follows:

Thank you, it works.
I've prepared _[ebuild]("http://git.kutkevich.org/gentoo-overlay.git/blob_plain/HEAD:/x11-wm/compiz/compiz-0.8.6-r3.ebuild")_ with this [_patch_]("http://git.kutkevich.org/gentoo-overlay.git/blob_plain/HEAD:/x11-wm/compiz/files/compiz-0.8.6-add-hjkl-vi-style-navigation-to-scale-plugin.patch") for Gentoo, Compiz 0.8.6.

---

