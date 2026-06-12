---
title: "Awn..."
date: 2008-12-22
forum: General Help
---

### Post by Alex4108 on 2008-12-22
I´m completely new to ubuntu and linux.  My friend told me to try out the mac theme and I figured out my ubuntu can look exactly like a mac.
I have the skin and got it to work, but the avant window navigator wont load...
If someone can help me out, I installed it from source, and got this error 
```
 ============================================================================
   ERROR!
   You probably have to install the development version of the Python package
   for your distribution.  The exact name of this package varies among them.
  ============================================================================

```:confused::confused:
I tried to install the dependancies and then got this
```

alex@Alex-Ubuntu:~/avant-window-navigator-0.2.6$ sudo apt-get install bzr libgtk2.0-dev libwnck-dev libwnck-common libgconf2-dev libglib2.0-dev libgnome2-dev libgnome-desktop-2  libgnome-desktop-dev libdbus-glib-1-dev gnome-common libxcomposite-dev libxdamage-dev librsvg2-dev libgtop2-dev libgnome-menu-dev libgnome-menu2 libgnome-menu-dev librsvg2.0-cil librsvg2-2 librsvg2-common librsvg2-dev libgtop2-7 libgtop2-common libgtop2-dev python-dev python-gtk2-dev python-cairo-dev python-gconf python-gnome2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libwnck-common is already the newest version.
Package libgnome-desktop-2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libgnome-desktop-2 has no installation candidate

```
Thanks for any help!

---

### Post by Wartender on 2008-12-22
try downloading awn from synaptic, it'll download everything you need and should install succesfully(search avant-window-navigator)

---

### Post by Alex4108 on 2008-12-22
Umm like I said Im completely new to linux... What is synaptic? I googled it but I´m confused on installing it

---

### Post by Wartender on 2008-12-22
right right ummm forgot... new to linux, go to system->administration->synaptic package manager

---

### Post by Alex4108 on 2008-12-22
Ok
I did that and searched for avant-window-navigator.
It pulled up a few things with AWN in the name, so I marked them all for installation, It installed, I did sudo avant-window-navigator and got this...
```

alex@Alex-Ubuntu:~/avant-window-navigator-0.2.6$ sudo avant-window-navigator
curves_symmetry unset, setting now
curviness unset, setting now
Error: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.

```

---

### Post by Wartender on 2008-12-22
you don't have compiz running?
try compiz --replace

---

### Post by Alex4108 on 2008-12-22
Yeah... I don´t even know what it is :P 
Im such a noob at this stuff
EDIT ->

```

alex@Alex-Ubuntu:~$ compiz --replace
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

```

Double Edit -> Downloading compiz right now

---

### Post by Wartender on 2008-12-22
how strange that you have to download it, it's usually already installed, oh well.

---

### Post by Alex4108 on 2008-12-22
yeah... Its installed now, I got the icon too, and now I guess run AWN again?

---

### Post by Wartender on 2008-12-22
yep, should work.

---

### Post by Alex4108 on 2008-12-22
UGHHHH
Okay
I started it up AGAIN and got this..
```

alex@Alex-Ubuntu:~$ sudo avant-window-navigator
Error: Screen isn't composited. Please run compiz (-fusion) or another compositing manager.

```

---

### Post by TVTrukChik on 2008-12-22
As a noob myself, I'm going to suggest that you install fusion-icon from Synaptic.  This will put a little icon on your top panel. You can right-click on the icon and see which window manager is active, and change between them.  Right-click, go to window manager, and select Compiz.  If your screen looks weird, try reloading the window manager by right-clicking that same icon and selecting Reload.

---

### Post by Alex4108 on 2008-12-22
and you think I didn´t do that? 
Yeah I already tried, anytime I try to do something with my icon, my screen goes white and I have to kill the power to my system and then turn it back on

---

### Post by TVTrukChik on 2008-12-22
Well, since an hour ago you said you didn't know what Synaptic was, no, I didn't think you'd done that... :-)

Do you know that you should be able to hit Ctrl-Alt-Backspace to restart the X window system?  Might save you from having to kill the power when your screen goes white.

Maybe saying what video card you have will give someone the info they need to help you.

---

### Post by GrandpaLeaman on 2008-12-22
```

alex@Alex-Ubuntu:~$ compiz --replace
Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

```It looks to me like your video card has been blacklisted. Go here to check:
[http://ubuntuforums.org/showthread.php?t=765875](http://ubuntuforums.org/showthread.php?t=765875)

Also, you may want to run compiz-check to see is Compiz will run with your video card. Go to the following thread to get the lowdown from Forlong, the Compiz guru:

[http://ubuntuforums.org/showthread.php?t=799070&highlight=compiz-check](http://ubuntuforums.org/showthread.php?t=799070&highlight=compiz-check)

I hope this helps! Have fun!!!

---

### Post by Alex4108 on 2008-12-23
Umm...
Im not exactly sure what my video card is
I have a Toshiba Tecra M4 Tablet if this helps

---

### Post by buzzbo on 2008-12-23
try google, Toshiba Tecra M4 Tablet specs

[second link and I see]("http://www.notebookreview.com/default.asp?newsID=2474") nVidia Go 6600 TE

---

### Post by buzzbo on 2008-12-23
also if you can't get compiz going, maybe try xcompmgr 

i.e.
sudo apt-get install xcompmgr

But it should be started before gnome ([see this thread]("http://ubuntuforums.org/showthread.php?t=33098"))

---

### Post by vanadium on 2008-12-23
There is a little secret I am going to share with you. metacity nowadays also supports compositing. You can therefore run awn on metacity if your graphics card is not supported by compiz.

Open gconf-editor. Navigate to /apps/metacity/general. Check "compositing_manager". Enjoy awn.

---

