---
title: "Stand alone program after boot"
date: 2011-11-02
forum: Desktop Environments
---

### Post by prchakal on 2011-11-02
Hi,

I have a project that i need start ubuntu or debian and after boot i need start a program made by mae using c++ and sfml/sdl, but i need disable all user interactive components from GUI, all that the user will see is my program after boot, and my program need use all thing from nvidia video card like when you in a normal environment (3d and accelerated).

How i can do it?

---

### Post by typhoon_tip on 2011-11-02
I think best way is to register your program as a Desktop component. In this way your user will login into it and it will take over entire desktop functionality. Your program need to manage entire screen drawing in this case, it cannot run in a window. You might want to take a look at XBMC and how they did their coding into a desktop app.

[http://xbmc.org/download/](http://xbmc.org/download/)

After installing XBMC, for instance, you get an entry in your login list and you can skip Unity or Gnome or else and login straight into XBMC. Your app need to manage shutdown/restart as well in this case, but that's easy because you can always rely on commands :P

---

### Post by prchakal on 2011-11-03
Hi,

I saw it, but the problem is how to initialize all drivers (video, sound, network, ...) without reinvent the wheel.

A simple solution is disable all gnome/unity bars, menus, windows and only start my app.

Today i put my app to start when unity start, but if i close the program i need all ubuntu desktop items :(

---

### Post by typhoon_tip on 2011-11-03
> **prchakal said:**
> Hi,

I saw it, but the problem is how to initialize all drivers (video, sound, network, ...) without reinvent the wheel.

A simple solution is disable all gnome/unity bars, menus, windows and only start my app.

Today i put my app to start when unity start, but if i close the program i need all ubuntu desktop items :(

First of all, try to open the program fully maximized as a "system modal" (property of Window Type for the main window), it should cover up everything else, apart from urgent error messages from the system.

---

### Post by lykwydchykyn on 2011-11-03
- set up a display manager for auto-login
- create a script to run your executable and (optionally) some minimal windowing environment.
- save the script as .xinitrc in the home directory of the user you're auto-logging in.  Give it execute permissions

Basically, a user's ~/.xinitrc file can override the desktop environment with whatever graphical applications are desired.

---

### Post by prchakal on 2011-11-03
Hi lykwydchykyn,

Is this what i want make.

But i need know how to make it "some minimal windowing environment".

Thanks, we are near the solution.

A friend give me it:
[http://users.telenet.be/mydotcom/howto/linuxsbs/xwin.htm](http://users.telenet.be/mydotcom/howto/linuxsbs/xwin.htm)

What you think?

---

### Post by lykwydchykyn on 2011-11-03
Well, you need xorg, of course, and *possibly* a window manager.  I've been using matchbox-window-manager for my kiosks, because it has no menus or panels or anything, and windows can't be minimized (it was designed for mobile devices, I think).

You could also use flwm, openbox, maybe awesome if you want to do a bit of lua hacking.

If your application is not prone to creating dialogs or extra windows, and will do full-screen nicely, you might not need a window manager.

I recently posted the .xinitrc file I use in my web kiosks at [this post](http://ubuntuforums.org/showpost.php?p=11410832&postcount=7).  See if that helps make sense of it.

---

### Post by prchakal on 2011-11-03
WOW!


@lykwydchykyn, your informations are very helpfull.

My application can open other programs and this other programs can be closed.

What happen if the LOOP of your xinitrc file end the loop?

Always will have my program running in background and my program will start other or not.

I need use nvidia or ati driver for 3d rendering, it depends of GDM? Or with any GDM i can use this drivers to render the 3d contents?

Thanks very much man.

---

### Post by lykwydchykyn on 2011-11-03
> **prchakal said:**
> WOW!


@lykwydchykyn, your informations are very helpfull.

Thanks
> 
My application can open other programs and this other programs can be closed.

You'll want a window manager then.  You might want to try out several to see which ones look and feel most natural with what you're doing.
> 
What happen if the LOOP of your xinitrc file end the loop?

In my case, it won't; because it's an infinite loop.  But basically, once the script reaches the end and exits, the session is done and the user is logged out.  Since I didn't want that to happen, I used the infinite loop.

Basically one (and only one) program should be the "blocker" that keeps the script from ending while the user is logged in.  You can use the window manager for this, if you want to use it's built in login/logout controls.  Anything that isn't the "blocker" should be forked into the background (with the ampersand symbol & ) and run first.

> 
Always will have my program running in background and my program will start other or not.

Probably you want it to be the "blocker" then, so run it last and don't append the ampersand.

> 
I need use nvidia or ati driver for 3d rendering, it depends of GDM? Or with any GDM i can use this drivers to render the 3d contents?

Thanks very much man.

GDM is not required for either of those drivers to work.  Any display manager should work just fine, though there's nothing wrong with using GDM if it does what you need.

I had trouble a while back with newer versions of GDM respecting the .xinitrc file, so that may be a consideration.  OTOH, it's always been the lightest DM that supports auto-login and timed login  (slim might support it now, but last time I tried it I couldn't make it work).

---

### Post by prchakal on 2011-11-03
Hi,

All apps that will be started will run in fullscreen mode.

With this observation i still need a window manager?

Thanks.

---

### Post by lykwydchykyn on 2011-11-03
> **prchakal said:**
> Hi,

All apps that will be started will run in fullscreen mode.

With this observation i still need a window manager?

Thanks.

You don't strictly need one, but without one any dialogs that popup are going to be awkwardly stuck up on one corner with no border.

Some programs don't want to full-screen properly without a window manager for some reason.

So really, you just need to try your application without a window manager, and if you observe awkward situations with the windows, try running it with one.  It's just a tool, you use it if you need it.

I've had good luck with matchbox because it stays out of the way, takes very few resources, but makes the occasional pop-up or dialog do what's expected.

Just try it both ways and see what you think.

---

### Post by prchakal on 2011-11-03
Ok, i will try.

But one thing that i dont understand in linux is if i need something EXTRA to start my app.

1 - Downloading debian clean now (i will construct all that i need from scratch).
2 - Will install some packages, like compiler, sfml libs, ...
3 - Dont will install any WM.
4 - Install SSH SERVER.
5 - Start my app.

---

### Post by lykwydchykyn on 2011-11-03
> **prchakal said:**
> Ok, i will try.

But one thing that i dont understand in linux is if i need something EXTRA to start my app.

1 - Downloading debian clean now (i will construct all that i need from scratch).
2 - Will install some packages, like compiler, sfml libs, ...
3 - Dont will install any WM.
4 - Install SSH SERVER.
5 - Start my app.

You need xorg, and you probably want a display manager to get you logged in.  There's something called "nodm" that is supposed to launch you straight into X without a desktop, but I had a lot of trouble with it, so I usually just use gdm with autologin configured.

---

### Post by prchakal on 2011-11-04
Hi,

I have installed everything but not a WM.

I have started xorg with "startx" and get the message:

> root@system-pc:/home/system/documents/cpp-libs/sfml# startx
xauth:  creating new authority file /root/.Xauthority


X.Org X Server 1.7.7
Release Date: 2010-05-04
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.32.29-dsa-ia32 i686 Debian
Current Operating System: Linux system-pc 2.6.32-5-686 #1 SMP Mon Oct 3 04:15:24 UTC 2011 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-5-686 root=UUID=160c762d-6241-40df-8ff1-0cec31af4331 ro quiet
Build Date: 19 February 2011  02:37:36PM
xorg-server 2:1.7.7-13 (Cyril Brulebois <kibi@debian.org>) 
Current version of pixman: 0.16.4
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Nov  4 02:54:22 2011
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) open /dev/fb0: No such file or directory
SELinux: Disabled on system, not enabling in X server

The console is blocked until i press CONTROL + C no quit it.

How i can test my application in this stage?


Thanks.

---

### Post by prchakal on 2011-11-04
I have some progress, my program is called, but the image is not showed:

The log:

> system@system-pc:~$ startx


X.Org X Server 1.7.7
Release Date: 2010-05-04
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.32.29-dsa-ia32 i686 Debian
Current Operating System: Linux system-pc 2.6.32-5-686 #1 SMP Mon Oct 3 04:15:24 UTC 2011 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.32-5-686 root=UUID=160c762d-6241-40df-8ff1-0cec31af4331 ro quiet
Build Date: 19 February 2011  02:37:36PM
xorg-server 2:1.7.7-13 (Cyril Brulebois <kibi@debian.org>) 
Current version of pixman: 0.16.4
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Fri Nov  4 03:07:09 2011
(==) Using system config directory "/usr/share/X11/xorg.conf.d"
(EE) open /dev/fb0: No such file or directory
SELinux: Disabled on system, not enabling in X server
Starting system, wait...


My **.xinitrc**:

> echo "Starting system, wait..."

xset s off
xset -dpms

# matchbox-window-manager &

while true; do
  # rsync -qr --delete /usr/local/kiosk/ /home/kiosk/
  /home/system/documents/solo-defender/bin/Debug/solo-defender
done

Only left now show the program interface, because everything at here is nice and my cooler start, so the video card is in use (this always happen in my mac).

---

### Post by prchakal on 2011-11-04
Hi,

The problem was solved :)

I forgot restart everything to take effect.

Now my program is running without any WM.

I dont test, but if i open another program like mine, it will start normally?

---

