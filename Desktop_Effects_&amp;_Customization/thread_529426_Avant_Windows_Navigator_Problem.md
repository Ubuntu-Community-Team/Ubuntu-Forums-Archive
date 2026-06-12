---
title: "Avant Windows Navigator Problem"
date: 2007-08-19
forum: Desktop Effects &amp; Customization
---

### Post by 5h4rk on 2007-08-19
When I open AWN, nothing happen, well, nothing that I can see. I have CF and have deleted the bottom panel.

---

### Post by SkiesOfAzel on 2007-08-19
Which version of awn do you have? Also try starting it from a terminal for more feedback .

---

### Post by Ozeuss on 2007-08-19
by CF, do you mean compiz fusion? are you sure compositing is enabled?

---

### Post by 5h4rk on 2007-08-19
It's version 0.1.2

From the terminal:

> 
chad@chad-laptop:~$ avant-window-navigator
APPLET : /usr/lib/awn/applets/taskman.desktop

(avant-window-navigator:7088): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:7088): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:7088): Wnck-WARNING **: Unhandled action type (nil)

...

New width = 58


Yes, by CF i meant Compiz Fusion.

---

### Post by SkiesOfAzel on 2007-08-19
Your version of awn is really old , Try getting awn from bazar . 
Uninstall the old version :
```
sudo apt-get remove avant-window*
``` 
Get the dependencies :
```
sudo apt-get install libgtk2.0-dev libwnck-dev libwnck-common libgconf2-dev libglib2.0-dev libgnome2-dev libgnome-desktop-2 libgnome-desktop-dev libdbus-glib-1-dev gnome-common libxcomposite-dev libxdamage-dev python-gnome2-desktop bzr automake1.9

```
Get awn :
```
bzr co http://bazaar.launchpad.net/~awn-core/awn/trunk avant-window-navigator
```
Compile :
```
cd avant-window-navigator
./autogen.sh && make && sudo make install
```
 And you are set.
If you need help with anything it's  better to ask on the [official awn forum]("http://www.planetblur.org/hosted/awnforum/index.php").

---

### Post by 5h4rk on 2007-08-19
I did what you said Skies, but still the same problem...

And I think I still ahve the old version, 0.1.2

> chad@chad-laptop:~$ aptitude show avant-window-navigator 
Package: avant-window-navigator
New: yes
State: not installed
Version: 0.1.2+svn20070731~3v1ubuntu0
Priority: optional
Section: eyecandy/desktop
Maintainer: Trevi <trevi55@gmail.com>
Uncompressed Size: 967k
Depends: libart-2.0-2 (>= 2.3.16), libatk1.0-0 (>= 1.13.1), libawn0,
         libbonobo2-0 (>= 2.15.0), libbonoboui2-0 (>= 2.15.1), libc6 (>=
         2.5-0ubuntu1), libcairo2 (>= 1.4.0), libdbus-1-3 (>= 0.94),
         libdbus-glib-1-2 (>= 0.73), libfontconfig1 (>= 2.4.0), libgconf2-4 (>=
         2.13.5), libglade2-0 (>= 1:2.5.1), libglib2.0-0 (>= 2.12.9),
         libgnome-desktop-2 (>= 2.11.1), libgnome-keyring0 (>= 0.7.1),
         libgnome2-0 (>= 2.14.1), libgnomecanvas2-0 (>= 2.11.1), libgnomeui-0
         (>= 2.17.1), libgnomevfs2-0 (>= 1:2.17.90), libgtk2.0-0 (>= 2.10.3),
         libice6 (>= 1:1.0.0), liborbit2 (>= 1:2.14.1), libpango1.0-0 (>=
         1.16.2), libpopt0 (>= 1.10), libsm6, libstartup-notification0 (>=
         0.8-1), libwnck18 (>= 2.15.90), libx11-6, libxcomposite1 (>= 1:0.3-1),
         libxcursor1 (> 1.1.2), libxdamage1, libxext6, libxfixes3 (>= 1:4.0.1),
         libxi6, libxinerama1, libxml2 (>= 2.6.27), libxrandr2 (>= 2:1.2.0),
         libxrender1, python, python-glade2
Description: Dock-like window navigator
 Avant Window Navgator (Awn) is a dock-like bar which sits at the bottom of the
 screen (in all its composited-goodness) tracking open windows. 
 
 This package contains the dockbar with applets 
 
 Homepage: [http://code.google.com/p/avant-window-navigator/](http://code.google.com/p/avant-window-navigator/)


And it says, "not installed", now I'm confused :(

---

### Post by SkiesOfAzel on 2007-08-19
It's probably not installed but the deb is still cashed so no worries. Do a sudo aptitude purge avant-window-navigator just to make certain and install the new version from bazaar.

---

### Post by 5h4rk on 2007-08-19
I don't know why, I did a sudo aptitude purge avant-window-navigator, but I still have it on my Applications menu, and if I open it without CF, I get a black rectangle...

and when I:

> 
chad@chad-laptop:~$ bzr co [http://bazaar.launchpad.net/~awn-core/awn/trunk](http://bazaar.launchpad.net/~awn-core/awn/trunk) avant-window-navigator
bzr: ERROR: Target directory "avant-window-navigator" already exists.


---

### Post by SkiesOfAzel on 2007-08-19
Open Synaptic , search for avant window , right click , select completely remove for the awn package(s) and hit apply.
 As for the second error, the problem is that there is already a folder named avant-window-navigator in your home folder. Either delete it or better make a packages dir to keep every app you install archived and in order.
```

 cd ~
mkdir packages
cd packages
mkdir awn
cd awn
mkdir 52
cd 52

```
The reason for the folder named 52 is that you might update latter to a version that gives you problems , so it's better to have the older versions in separate folders and revert to them when you need to.

---

### Post by SkiesOfAzel on 2007-08-19
Also , did you have errors when you tried to compile from bazaar? If you didn't then you probably already have the latest version and you just need to configure it.

---

### Post by 5h4rk on 2007-08-19
I can't remove avant-window-navigator from Synaptic because it's not installed. :S

By compiling from bazaar, you mean "bzr co [http://bazaar.launchpad.net/~awn-core/awn/trunk](http://bazaar.launchpad.net/~awn-core/awn/trunk) avant-window-navigator", nop, no errors were shown...

BTW, what does "compiling from bazaar" mean? what is bazaar?

thanks for your help

and also, i have system > preference > awn manager

:S

---

### Post by SkiesOfAzel on 2007-08-19
Bazaar is a version control system for software in developement.
this line
bzr co [http://bazaar.launchpad.net/~awn-core/awn/trunk](http://bazaar.launchpad.net/~awn-core/awn/trunk) avant-window-navigator
gets you the source code.
then you have to configure the source to properly compile for your system with 
./autogen.sh
if after you input the later there are messages about errors or missing packages it means you have to find and install the missing packages (which are needed for the software to run) before you can proceed. 
You compile with
make
Compiling is the procedure that converts the text code of your software to machine code that can run in your pc. 
If you get errors after make it means that something went wrong
If all went well you install with 
sudo make install
.
Since you have awn manager installed it probably means that all went well and awn is now installed on your system.
If you still can't see it after running it, open awn manager , select applets, add the launcher/taskmanager applet and hit refresh.
if you still can't see awn, do this :
```

sudo apt-get install gconf-editor
gconf-editor

```
Goto apps -> avant window navigator.
Click force monitor and set monitor_height and monitor_width acording to your monitor resolution.

---

### Post by 5h4rk on 2007-08-19
Mmm, can't make it work :(

Now I have Avant preferences AND awn manager under system...

How can I delete everything and do install it again?

Thanks.

---

### Post by reacocard on 2007-08-19
> **5h4rk said:**
> Mmm, can't make it work :(

Now I have Avant preferences AND awn manager under system...

How can I delete everything and do install it again?

Thanks.

try this guide here: [http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)

just follow the source part, then when you get to 
```
bzr checkout http://bazaar.launchpad.net/~awn-core/awn/trunk avant-window-navigator
cd avant-window-navigator
./autogen.sh
make
sudo make install
```

do this instead:
```
bzr checkout http://bazaar.launchpad.net/~awn-core/awn/trunk avant-window-navigator
cd avant-window-navigator
./autogen.sh
sudo make uninstall
```
that will clear out the old stuff, then simply proceed to either follow the source install or repo install instructions from that guide.

hope this helps!

---

### Post by 5h4rk on 2007-08-30
I did uninstall it successfully, and also have reinstall it using this guide:

[http://awn.wetpaint.com/page/Ubuntu+Feisty+Repository?t=anon](http://awn.wetpaint.com/page/Ubuntu+Feisty+Repository?t=anon)

But still can not run it.

I'm running CF btw.

This is the output:

> 
chad@chad-laptop:/$ avant-window-navigator
APPLET : /usr/lib/awn/applets/taskman.desktop
APPLET : /usr/local/lib/awn/applets/trash.desktop

(avant-window-navigator:9843): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:9843): Wnck-WARNING **: Unhandled action type (nil)

** (awn-applet-activation:9845): WARNING **: This desktop file does not exist /usr/local/lib/awn/applets/trash.desktop


(avant-window-navigator:9843): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:9843): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:9843): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:9843): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:9843): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:9843): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:9843): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:9843): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:9843): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:9843): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:9843): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:9843): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:9843): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:9843): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:9843): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:9843): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:9843): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:9843): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:9843): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:9843): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:9843): Wnck-WARNING **: Unhandled action type (nil)

(avant-window-navigator:9843): Wnck-WARNING **: Unhandled action type (nil)



and also what is the difference if I do:

sudo apt-get install avant-window-navigator-bzr

and

sudo apt-get install avant-window-navigator

?

Thanks.

---

### Post by ArtF10 on 2007-08-30
I think that people who do get AWM to work MUST post their system specs, especially graphic card specs.

[http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981)

is really confusing because it says AWN is not stable and pretty much stalls there....where do you get the bzr version?  I've tried to install it WITH Compiz Fusion from Trevino's repositories and ALL it did was produce a white bar at the bottom of the screen (I deleted the bottom panel) and nothing else happened.

From my experience with it, fOR what is called THE "best" Linux dock, it sure sucks.

---

### Post by praet on 2007-08-30
Try checking that your window resolution was read correctly by avant when you installed it.
open:
```
gconf-editor
```

Enabling this key will try to auto set it on every launch:
```
/apps/avant-window-navigator/force_monitor
```

The pre-set width and height of the monitor are here too:
```
/apps/avant-window-navigator/monitor_height
/apps/avant-window-navigator/monitor_width
```

---

### Post by 5h4rk on 2007-08-30
ah, I have dual screen btw, with different resolution.

the bzr i got it from here

[http://awn.wetpaint.com/page/Ubuntu+Feisty+Repository?t=anon](http://awn.wetpaint.com/page/Ubuntu+Feisty+Repository?t=anon)

I just removed everything and follow that guide, but doesnt work for me, not yet...

---

### Post by ArtF10 on 2007-08-30
> **5h4rk said:**
> ...[http://awn.wetpaint.com/page/Ubuntu+Feisty+Repository?t=anon](http://awn.wetpaint.com/page/Ubuntu+Feisty+Repository?t=anon)......

Allow me to quote a line from that website:

"NOTICE: No stable AWN at this time. It will be added at the next release."

---

### Post by 5h4rk on 2007-08-30
> **ArtF10 said:**
> Allow me to quote a line from that website:

"NOTICE: No stable AWN at this time. It will be added at the next release."

but the problem is not this, the problem is that lots of people can make it work but me :(

---

