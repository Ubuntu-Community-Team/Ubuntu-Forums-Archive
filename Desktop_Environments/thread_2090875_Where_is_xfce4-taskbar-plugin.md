---
title: "Where is xfce4-taskbar-plugin?"
date: 2012-12-03
forum: Desktop Environments
---

### Post by mp035 on 2012-12-03
Hi I am trying to find the xfce4-taskbar-plugin.  It has the ability (among other things) to "stick" an application to the taskbar, similar to how a dock works.  A picture of it and a reference to it are here:

[http://goodies.xfce.org/projects/panel-plugins/xfce4-taskbar-plugin]("http://goodies.xfce.org/projects/panel-plugins/xfce4-taskbar-plugin")

The page says it is included with the panel after 4.4, but I cant find it on xfce 4.10, and I cant find it in the xfce-goodies package either.

Does anyone know how to get it?

---

### Post by slickymaster on 2012-12-03
All of your .desktop files for your panel plugins can be found in the directory **/usr/share/xfce4/**

For the taskbar just type at a terminal the following code:

```
$ sudo apt-get install xfce4-taskbar-plugin
```

---

### Post by mp035 on 2012-12-03
Hi stickymaster,
Thanks for the reply, but that was the first thing I tried.  I tried it again just in case:
```

mark@mark-laptop:~$ sudo apt-get install xfce4-taskbar-plugin
[sudo] password for mark: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package xfce4-taskbar-plugin
mark@mark-laptop:~$ 

```

Do I need a special repository?

---

### Post by slickymaster on 2012-12-04
Downloaded it from [here]("http://git.xfce.org/panel-plugins/xfce4-taskbar-plugin/snapshot/xfce4-taskbar-plugin-master.tar.bz2") and use ```
sudo checkinstall
``` instead of ```
sudo make install
``` to install it. That should solve it for you.

---

### Post by LewisTM on 2012-12-04
Sorry for intruding but I don't understand this topic.
The link you posted clearly states that the plugin is now part of xfce4-panel. It most likely corresponds to the Window buttons panel item, which provides the classic taskbar. By the way, 4.10 > 4.4. Don't ask :)

The "Stick" menu item makes a window sticky i.e. always present on the current workspace. It does not turn your taskbar into a dock. It was renamed "Always on visible workspace" for a good reason, "Stick" is clearly too cryptic.

---

### Post by mp035 on 2012-12-04
Thanks slickymaster, that did it!!!!!!

@LewisTM you are incorrect, the current version of taskbar-plugin will show up as Task Bar (Windows 7 Task Bar Mimick) in the "Add New Items" dialog for the XFCE panel.  It is not the same as window buttons. 

for anyone else looking for a "dock" for the xfce panel, I bzippped the created deb file and attached it to this post (sorry but debs are not allowed to be attached so I had to bzip it).

NOTE BEWARE OF UNAUTHORIZED DEBS (EVEN THE ONE ATTACHED) AND USE AT YOUR OWN RISK.

Edit: Attachment removed, see below for a binary archive and installation instructions.

---

### Post by LewisTM on 2012-12-04
I stand corrected and would love to give the plugin a try.
Am I flipping or does your deb not contain binaries? I couldn't compile them, would you care to share them?

---

### Post by mp035 on 2012-12-05
Sorry LewisTM, for some reason checkinstall did not include the binaries.  I changed Makefile so that the libraries were copied rather than linked, but still no luck.

I have attached a tar.gz with the 2 required files inside, unpack it, and then run the following:
```

sudo cp `pwd`/libtaskbar.so /usr/lib/xfce4/panel-plugins/libtaskbar.so
sudo cp `pwd`/taskbar.desktop /usr/share/xfce4/panel/plugins/taskbar.desktop

```

and all should be well.  

BTW, I love your signature.

Others note, this has been compiled on xubuntu 12.10 for AMD64

---

### Post by slickymaster on 2012-12-05
[QUOTE=mp035;12388393]Thanks slickymaster, that did it!!!!!!

I'm glad I helped.

---

### Post by LewisTM on 2012-12-05
Works, Thanks!
So they did change the terminology from 'Stick' to 'Pin this program to the taskbar'. hehe

I agree that it should be part of Xfce goodies. It's definitely a nice lightweight dock solution and could even be developed to support some Unity features like quicklists and dynamic icons.

---

### Post by matti82 on 2012-12-11
I can't get this plugin running. If I try to compile it, I get many errors, and if I try to use the binary package provided here, I get an error message when I add the plugin to the panel. Has anyone any idea how to fix this?

---

### Post by LewisTM on 2012-12-11
Are you running Xubuntu 12.10 64 bit? I doubt the compiled plugin will work in other environments and architectures.

It's also a good idea to share the error message. Don't hold any information back :)

---

### Post by matti82 on 2012-12-11
I tried the binary package on Xubuntu 11.10, 12.10 and Debian wheezy (all 64 bit). There is no useful error message, there is only a popup that tells that the taskbar plugin has been restarted several times and asks if I want to retry or remove the plugin. Clicking on retry doesn't help.

---

### Post by sherby on 2013-04-12
Can someone help me to install this from source(total newbie)?

I extracted the tar to folder, right click open terminal here, type make and i get this
```
saved@saved-MM061:/usr/local/src/xfce4-taskbar-plugin-master$ make
cc -fPIC -DPACKAGE_NAME="\"Taskbar\"" -DLC_MESSAGES="\"C\"" -DHELPDIR="\"/usr/share/doc/xfce4-taskbar/\"" -g -I. `pkg-config --cflags-only-I gtk+-2.0 exo-1 libwnck-1.0 libxfce4panel-1.0 libxfce4ui-1 libxfconf-0 gtkhotkey-1.0`   -c -o taskbar.o taskbar.c
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
Package exo-1 was not found in the pkg-config search path.
Perhaps you should add the directory containing `exo-1.pc'
to the PKG_CONFIG_PATH environment variable
No package 'exo-1' found
Package libwnck-1.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libwnck-1.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libwnck-1.0' found
Package libxfce4panel-1.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libxfce4panel-1.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libxfce4panel-1.0' found
Package libxfce4ui-1 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libxfce4ui-1.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libxfce4ui-1' found
Package libxfconf-0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libxfconf-0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libxfconf-0' found
Package gtkhotkey-1.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtkhotkey-1.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtkhotkey-1.0' found
taskbar.c:6:21: fatal error: exo/exo.h: No such file or directory
compilation terminated.
make: *** [taskbar.o] Error 1
saved@saved-MM061:/usr/local/src/xfce4-taskbar-plugin-master$ 


```

later checkinstall gets this

```
checkinstall 1.6.2, Copyright 2009 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.



*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@saved-MM061 ]
1 -  Summary: [ Package created with checkinstall 1.6.2 ]
2 -  Name:    [ xfce4-taskbar-plugin ]
3 -  Version: [ master ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ xfce4-taskbar-plugin-master ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]
11 - Provides: [ xfce4-taskbar-plugin ]
12 - Conflicts: [  ]
13 - Replaces: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
sudo ln -s `pwd`/libtaskbar.so /usr/lib/xfce4/panel-plugins/libtaskbar.so
ln: failed to create symbolic link `/usr/lib/xfce4/panel-plugins/libtaskbar.so': File exists
make: *** [install] Error 1

****  Installation failed. Aborting package creation.

Restoring overwritten files from backup...OK

Cleaning up...OK

Bye.


```

---

### Post by slickymaster on 2013-04-12
> **sherby said:**
> Can someone help me to install this from source(total newbie)?

I extracted the tar to folder, right click open terminal here, type make and i get this
```
saved@saved-MM061:/usr/local/src/xfce4-taskbar-plugin-master$ make
cc -fPIC -DPACKAGE_NAME="\"Taskbar\"" -DLC_MESSAGES="\"C\"" -DHELPDIR="\"/usr/share/doc/xfce4-taskbar/\"" -g -I. `pkg-config --cflags-only-I gtk+-2.0 exo-1 libwnck-1.0 libxfce4panel-1.0 libxfce4ui-1 libxfconf-0 gtkhotkey-1.0`   -c -o taskbar.o taskbar.c
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
Package exo-1 was not found in the pkg-config search path.
Perhaps you should add the directory containing `exo-1.pc'
to the PKG_CONFIG_PATH environment variable
No package 'exo-1' found
Package libwnck-1.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libwnck-1.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libwnck-1.0' found
Package libxfce4panel-1.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libxfce4panel-1.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libxfce4panel-1.0' found
Package libxfce4ui-1 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libxfce4ui-1.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libxfce4ui-1' found
Package libxfconf-0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libxfconf-0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libxfconf-0' found
Package gtkhotkey-1.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtkhotkey-1.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtkhotkey-1.0' found
taskbar.c:6:21: fatal error: exo/exo.h: No such file or directory
compilation terminated.
make: *** [taskbar.o] Error 1
saved@saved-MM061:/usr/local/src/xfce4-taskbar-plugin-master$ 


```

later checkinstall gets this

```
checkinstall 1.6.2, Copyright 2009 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.



*****************************************
**** Debian package creation selected ***
*****************************************

This package will be built according to these values: 

0 -  Maintainer: [ root@saved-MM061 ]
1 -  Summary: [ Package created with checkinstall 1.6.2 ]
2 -  Name:    [ xfce4-taskbar-plugin ]
3 -  Version: [ master ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ xfce4-taskbar-plugin-master ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]
11 - Provides: [ xfce4-taskbar-plugin ]
12 - Conflicts: [  ]
13 - Replaces: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
sudo ln -s `pwd`/libtaskbar.so /usr/lib/xfce4/panel-plugins/libtaskbar.so
ln: failed to create symbolic link `/usr/lib/xfce4/panel-plugins/libtaskbar.so': File exists
make: *** [install] Error 1

****  Installation failed. Aborting package creation.

Restoring overwritten files from backup...OK

Cleaning up...OK

Bye.


```

Even though you dealing with issues with xfce4-taskbar, I think it would be advisable for you to start a new thread since this one is already marked as SOLVED and because of that you'll probably won't get as much help as you would expect.

Just one last note, please post the output of:
```
uname -a
```
at the new thread. The reason why is because the solution in this thread has been compiled on xubuntu 12.10 for AMD64 and we need to know what's your system and hardware specs.
One last thing, in your first block of code you have several reports of missing packages. Confirm you have them by running:
```
dpkg --get-selections | grep name_of_package
```
If you don't have them, you have to install them prior to installing xfce4-taskbar.plugin.

---

### Post by sherby on 2013-04-13
I got it to work, i was doing make devenv outside the folder.... >.< I feel silly now.

---

