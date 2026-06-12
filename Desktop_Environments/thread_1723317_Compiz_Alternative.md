---
title: "Compiz Alternative"
date: 2011-04-06
forum: Desktop Environments
---

### Post by XsheepX on 2011-04-06
I'm trying to find some 3d cube and/or wobbly windows apps that aren't compiz, for my other distros whose environment conflicts with compiz (openbox).
Any help or suggestions would be much appreciated. :)

---

### Post by Zorgoth on 2011-04-06
Kwin (KDE) does those as well.  I am not aware of any other window manager with those features, but I don't know for sure.

---

### Post by XsheepX on 2011-04-07
> **Zorgoth said:**
> Kwin (KDE) does those as well.  I am not aware of any other window manager with those features, but I don't know for sure.

Thank you, but i'm looking for something more like an app that doesn't require a specific environment.

---

### Post by XsheepX on 2011-04-10
Bump

---

### Post by Enigmapond on 2011-04-10
What you are looking for is environment related. TMK there is no application that will do this only desktop environments.

---

### Post by Simian Man on 2011-04-10
Compiz is a window manager.  When you enable desktop effects in Gnome, what you are really doing is replacing the default window manager (metacity), with compiz.  Because openbox is another window manager, it is not possible to run it at the same time.

There was something called xcompmgr that could add some effects like shadows and transparency to another window manager, but I don't know if it has been maintained - and it certainly can't do desktop cube or wobbly windows or anything like that.

If you want barebones, use Openbox.  If you want pizazz, use Compiz or Kwin.

---

### Post by ~Plue on 2011-04-10
theres cairo-compmgr. it could do menu/window animations, add shadows, and a flashy application switcher,etc....(and it seems smoother than xcompmgr)

//btw, no cube or wobbly windows

---

### Post by Copper Bezel on 2011-04-10
Good call. I couldn't remember the name of that one, either.

XsheepX, are you using LXDE, or just Openbox by itself?

---

### Post by XsheepX on 2011-04-10
> **Copper Bezel said:**
> Good call. I couldn't remember the name of that one, either.

XsheepX, are you using LXDE, or just Openbox by itself?
I'm using Crunchbang, which uses the Openbox manager.

---

### Post by Copper Bezel on 2011-04-10
Would [_this_]("http://crunchbanglinux.org/forums/post/4029/#p4029") work for your situation?

---

### Post by XsheepX on 2011-04-10
> **Copper Bezel said:**
> Would [_this_]("http://crunchbanglinux.org/forums/post/4029/#p4029") work for your situation?
Thanks, I came very close to getting it running, but every time I tried to run the Compiz standalone, the session would automatically exit. I could get the Compiz Config Settings Manager to run, but nothing I did would go into effect.

---

### Post by Copper Bezel on 2011-04-10
Huh. I'm actually running Standalone with Gnome parts on my machine - some very helpful folks in this forum guided me through in baby steps, and the [Ubuntu wiki documentation]("https://help.ubuntu.com/community/CompizStandalone") helped. It's a fun new toy.

#! is Ubuntu-based, right? The process should be similar. You might look at the Preferences -> Profile settings for Compiz, particularly the backend.

At what point does the session exit? And what does the startup script look like?

(This is all assuming that simply enabling xcompmanager or installing cairo-compmanager isn't sounding like a better option. = )

---

### Post by XsheepX on 2011-04-12
> **Copper Bezel said:**
> Huh. I'm actually running Standalone with Gnome parts on my machine - some very helpful folks in this forum guided me through in baby steps, and the [Ubuntu wiki documentation]("https://help.ubuntu.com/community/CompizStandalone") helped. It's a fun new toy.
 
#! is Ubuntu-based, right? The process should be similar. You might look at the Preferences -> Profile settings for Compiz, particularly the backend.
 
At what point does the session exit? And what does the startup script look like?
 
(This is all assuming that simply enabling xcompmanager or installing cairo-compmanager isn't sounding like a better option. = )
 When I run CCSM in the terminal, the application works, but none of the effects I enable actually work or do anything. When I run "compiz ccp", it tells me another window manager is in use, so I use "compiz ccp --replace", and it immediately logs me out when I hit enter. I installed everything on the guide you linked except for Jockey-gtk, because it couldn't locate the package, becaues there is no jockey-gtk for Debian. So, I installed the nvidia settings manager directly, since jockey wasn't an option. Still no luck.
 
On a side note, I found some app that does 3d cube effects, similar to compiz:
[http://desk3d.sourceforge.net/](http://desk3d.sourceforge.net/)
Although, it appears to not do anything at all after I installed the debian package.

---

### Post by Copper Bezel on 2011-04-12
Since 3D-desktop is no longer in development, it probably isn't compatible with a modern #! install.

In any event, running ccsm will set up your Compiz effects, but it won't have any effect on Openbox. Running compiz -ccp --replace from an Openbox session kills Openbox, which ends the session. (If I'm understanding this stuff correctly, every session depends on something to hold it open; think of a shell script, which can call out to other processes along the way but will remain running until its *own* last process quits, at which point it returns to a command prompt.) 

So we can't run Compiz in an Openbox session, but what we want to do is give you a login option at GDM for a Compiz session as opposed to an Openbox one. It looks complicated, but it's actually a fairly quick process.

I should have linked this before, but I found [_one guide specifically for #!_]("http://crunchbanglinux.org/forums/topic/2827/howto-run-compiz-as-a-standalone-window-manager/") as well. However, since #! uses GDM and it's based on current Ubuntu packages, this process should work the same as it did on my machine, so I'll reproduce the scripts I'm using here.

They're in three parts chained together, a launcher and two scripts that need to be marked as executable. The first (the launcher) adds the session to the menu in GDM.

Create the file /usr/share/xsessions/Fusion:
```
[Desktop Entry]
Encoding=UTF-8
# This is the name you'll see for the session in gdm
Name=Fusion
# This is the comment
Comment=Compiz Fusion Standalone
# The command
Exec=/usr/local/bin/start-fusion.sh
Type=Application
```

The second is the session itself. When this script ends, the session ends and you return to GDM, so the sleep process should hold the session open until you run pkill sleep, which you can use as a menu item to log out.

So, in /usr/local/bin/start-fusion.sh:
```
#!/bin/bash
compiz ccp &
emerald &
~/.fusion-startup &
sleep 366d
```

Emerald is of course a bit heavy for your purposes, but there are [_other decorators_]("http://wiki.compiz.org/Decorators/GTKWindowDecorator") you might look into; Cairo's looks line a nice match.

The third script launches user startup applications. Not much of mine likely applies to you:

In ~.fusion-startup:
```
#!/bin/bash
gnome-settings-daemon &
nm-applet --sm-disable &
avant-window-navigator &
tomboy --tray-icon &
dropbox start -i
```

But this is where you could include tint2, #!'s settings service, nm-applet, feh, etc. (I'm using Compiz wallpaper, but it has an odd bug with a very annoying fix in recent versions of Ubuntu.)

If you want to keep tint2, one thing I hadn't considered is that you'd need [compiz-boxmenu]("https://aur.archlinux.org/packages.php?ID=46428"), which is more or less a clone of Openbox's pipemenu for Compiz. On the other hand, lxpanel seems to provide both, so it might be a simpler option.

---

### Post by XsheepX on 2011-04-12
> **Copper Bezel said:**
> Since 3D-desktop is no longer in development, it probably isn't compatible with a modern #! install.

In any event, running ccsm will set up your Compiz effects, but it won't have any effect on Openbox. Running compiz -ccp --replace from an Openbox session kills Openbox, which ends the session. (If I'm understanding this stuff correctly, every session depends on something to hold it open; think of a shell script, which can call out to other processes along the way but will remain running until its *own* last process quits, at which point it returns to a command prompt.) 

So we can't run Compiz in an Openbox session, but what we want to do is give you a login option at GDM for a Compiz session as opposed to an Openbox one. It looks complicated, but it's actually a fairly quick process.

I should have linked this before, but I found [_one guide specifically for #!_]("http://crunchbanglinux.org/forums/topic/2827/howto-run-compiz-as-a-standalone-window-manager/") as well. However, since #! uses GDM and it's based on current Ubuntu packages, this process should work the same as it did on my machine, so I'll reproduce the scripts I'm using here.

They're in three parts chained together, a launcher and two scripts that need to be marked as executable. The first (the launcher) adds the session to the menu in GDM.

Create the file /usr/share/xsessions/Fusion:
```
[Desktop Entry]
Encoding=UTF-8
# This is the name you'll see for the session in gdm
Name=Fusion
# This is the comment
Comment=Compiz Fusion Standalone
# The command
Exec=/usr/local/bin/start-fusion.sh
Type=Application
```

The second is the session itself. When this script ends, the session ends and you return to GDM, so the sleep process should hold the session open until you run pkill sleep, which you can use as a menu item to log out.

So, in /usr/local/bin/start-fusion.sh:
```
#!/bin/bash
compiz ccp &
emerald &
~/.fusion-startup &
sleep 366d
```

Emerald is of course a bit heavy for your purposes, but there are [_other decorators_]("http://wiki.compiz.org/Decorators/GTKWindowDecorator") you might look into; Cairo's looks line a nice match.

The third script launches user startup applications. Not much of mine likely applies to you:

In ~.fusion-startup:
```
#!/bin/bash
gnome-settings-daemon &
nm-applet --sm-disable &
avant-window-navigator &
tomboy --tray-icon &
dropbox start -i
```

But this is where you could include tint2, #!'s settings service, nm-applet, feh, etc. (I'm using Compiz wallpaper, but it has an odd bug with a very annoying fix in recent versions of Ubuntu.)

If you want to keep tint2, one thing I hadn't considered is that you'd need [compiz-boxmenu]("https://aur.archlinux.org/packages.php?ID=46428"), which is more or less a clone of Openbox's pipemenu for Compiz. On the other hand, lxpanel seems to provide both, so it might be a simpler option.

Okay, I created the GDM login, and I can get in it, but there it's totally bare; no way of opening a terminal or right-clicking to get my main menu. Do you happen to know what I should add to the startup scripts to get these things?

Here's what my start-fusion.sh looks like:
```

#!/bin/bash
compiz ccp &
~/.fusion-startup &
lxsession &
nitrogen --restore &
sleep 366d

```

Thank you.

---

### Post by Copper Bezel on 2011-04-12
No problem, and thank *you*. I mean, if you were seeing the papers I'm avoiding grading.... = )

Odd. I commented out everything in my  start-fusion.sh and replaced it with what you have there, minus my ~/.fusion-startup, and I found myself (*very* rapidly) logged into a vanilla LXDE session. I had lxpanel, but also xfwm (!) as the window manager and pacmanfm as the desktop. Compiz --replace did work from there.

I know it's affected by that weird user-wide startup list, since lxsession loads that, but that doesn't account for why I would have lxpanel and you wouldn't.

I would try forcing lxpanel and toss in your preferred terminal emulator just to be safe, both in the second startup script in your home directory. Then we can start to figure out what is and isn't loading where.

Edit: And I'm now wondering, why *xfwm*, of all things ...?

Another Edit: If you try adding lxpanel, let's try it without lxsession in the startup. I think it's creating a conflict somewhere, and we'll figure out how to load your system settings after we figure out how to get anything running at all.

---

### Post by XsheepX on 2011-04-13
> **Copper Bezel said:**
> No problem, and thank *you*. I mean, if you were seeing the papers I'm avoiding grading.... = )

Odd. I commented out everything in my  start-fusion.sh and replaced it with what you have there, minus my ~/.fusion-startup, and I found myself (*very* rapidly) logged into a vanilla LXDE session. I had lxpanel, but also xfwm (!) as the window manager and pacmanfm as the desktop. Compiz --replace did work from there.

I know it's affected by that weird user-wide startup list, since lxsession loads that, but that doesn't account for why I would have lxpanel and you wouldn't.

I would try forcing lxpanel and toss in your preferred terminal emulator just to be safe, both in the second startup script in your home directory. Then we can start to figure out what is and isn't loading where.

Edit: And I'm now wondering, why *xfwm*, of all things ...?

Another Edit: If you try adding lxpanel, let's try it without lxsession in the startup. I think it's creating a conflict somewhere, and we'll figure out how to load your system settings after we figure out how to get anything running at all.
Well, I tried it, and all the applications had no border around them. So, I took out lxpanel and put lxde instead. I was able to get borders and whatnot, but I still couldn't get compiz to work, or replace with it. So I installed blackbox, fluxbox, and pekwm. Tried them all, one-by-one; no dice.

The main reason why I'm trying to get compiz to run on crunchbang is so I can have the customizable main menu for a right-click. If I could find a way to do this in Ubuntu, I would just do it instead. (I don't use panels because I like my desktop to look extremely minimalistic; I've been using the MintMenu as a main menu.)

Edit: Here's my current desktop: [IMG]http://img13.imageshack.us/img13/8125/screenshotgw.png[/IMG]

---

### Post by Copper Bezel on 2011-04-13
Hmm. Odd. The window borders aren't drawn by Compiz, but it will ordinarily run a fallback decorator (emerald or cairo) if it can't work with the one running. (Actually, [I screwed up]("http://wiki.compiz.org/Decorators/GTKWindowDecorator"), looking at the wiki. Outside of Gnome, emerald is the only decorator Compiz can run, at least without some hacking. Annoying, because Cairo-decorator is the one we want - very Openbox-looking and featherweight.)

But hey, it means that we got Compiz working as the WM, which means we're close. = )

Piped menus like that are *sort of* available for Compiz: [Compiz Boxmenu]("http://sourceforge.net/projects/compizboxmenu/"). I think it has to be set to a Compiz binding, though (like a corner click, as opposed to just right-clicking the desktop.)

I'm starting not to be sure if we can make this work without Emerald, and I don't know whether that's too heavy for your requirements, as it's pretty much *the *least minimalist decorator there is.

[Edited for various corrections.]

---

### Post by XsheepX on 2011-04-13
> **Copper Bezel said:**
> Hmm. Odd. The window borders aren't drawn by Compiz, but it will ordinarily run a fallback decorator (emerald or cairo) if it can't work with the one running. (Actually, [I screwed up]("http://wiki.compiz.org/Decorators/GTKWindowDecorator"), looking at the wiki. Outside of Gnome, emerald is the only decorator Compiz can run, at least without some hacking. Annoying, because Cairo-decorator is the one we want - very Openbox-looking and featherweight.)

But hey, it means that we got Compiz working as the WM, which means we're close. = )

Piped menus like that are *sort of* available for Compiz: [Compiz Boxmenu]("http://sourceforge.net/projects/compizboxmenu/"). I think it has to be set to a Compiz binding, though (like a corner click, as opposed to just right-clicking the desktop.)

I'm starting not to be sure if we can make this work without Emerald, and I don't know whether that's too heavy for your requirements, as it's pretty much *the *least minimalist decorator there is.

[Edited for various corrections.]
Oh, this machine can handle it, it's just that crunchbang won't locate the package for emerald. This current machine has 6gb of ddr3 ram, the i7 920 dual quad core at 2.67ghz, 4gb of gddr5 ram, and two nvidia geForce GTX 260's, each having like 650 mhz core clock speed and like 1.2 ghz memory speed.
So, yeah, it can handle it like a dream, it's just that I can never get crunchbang to locate the package; even if I go download the Debian package for it, the dependencies are not satisfiable and it won't let me install it :\

---

### Post by Copper Bezel on 2011-04-13
Oh, duh. I'm terrible at this. I thought we needed gconf to select a Compiz decorator, but we don't. What happens from within Standalone if you run gtk-window-decorator ?

---

### Post by XsheepX on 2011-04-14
> **Copper Bezel said:**
> Oh, duh. I'm terrible at this. I thought we needed gconf to select a Compiz decorator, but we don't. What happens from within Standalone if you run gtk-window-decorator ?
 It says there's no command, so I tried looking for gtk-wndow-manager to install it, but it can't locate the package.

---

### Post by Copper Bezel on 2011-04-14
Hrng. It's supposed to be included with Compiz. Do you have the Compiz extras packages installed? I guess it's possible it's in there (but it seems unlikely to me.)

---

### Post by Krytarik on 2011-04-14
It's in the package "compiz-gnome", at least for Ubuntu. (I was following this thread right from the start, but I can't really help because I don't really know Crunchbang.)

Greetings.

---

### Post by Copper Bezel on 2011-04-14
I don't have any experience with Crunchbang, either; the guide made it look quite a bit simpler than it is. In retrospect, it would have been much simpler than starting with Crunchbang and building up to start with Gnome Ubuntu or Xubuntu and tear down (and *that* I at least have some experience with.) It looks like compiz-gnome has Gnome as a dependency, too. Damn.

---

### Post by XsheepX on 2011-04-14
> **Copper Bezel said:**
> I don't have any experience with Crunchbang, either; the guide made it look quite a bit simpler than it is. In retrospect, it would have been much simpler than starting with Crunchbang and building up to start with Gnome Ubuntu or Xubuntu and tear down (and *that* I at least have some experience with.) It looks like compiz-gnome has Gnome as a dependency, too. Damn.
Hmm, well maybe we could just replace nautilus with something else. In Crunchbang, I could use nautilus as just an application, and not alter my window manager. Maybe we can find a WM that will work with compiz, to achieve a right-click menu in Ubuntu.

---

### Post by Copper Bezel on 2011-04-14
It's just kind of weird. We have ostensible screencap evidence of someone making this work.

Yuck. I guess I'd start with Xubuntu, I think, if you really want to go through with this. That gives us a lightweight settings manager, and we can install Compiz and the decorator of your choice on that, grab Compiz Boxmenu for the right-click pipe menu, and keep Nitrogen for the wallpaper and pcman-fm (or Thunar if you'd prefer it) for the file manager.

I guess [this guy]("http://crunchbanglinux.org/forums/topic/2827/howto-run-compiz-as-a-standalone-window-manager/") really did start from Ubuntu rather than Crunchbang, too, so it's fairly misleading. I do find it weird that there are so very many things that we can't seem to install in Crunchbang.

Oh, on Nautilus: it only draws a desktop if your gconf settings tell it to do so, and you don't have gconf settings under Crunchbang at all. With those settings changed, it's the same on my machine (Nautilus does not try to draw a desktop or continue run in the background when closed.)

---

### Post by XsheepX on 2011-04-14
> **Copper Bezel said:**
> It's just kind of weird. We have ostensible screencap evidence of someone making this work.

Yuck. I guess I'd start with Xubuntu, I think, if you really want to go through with this. That gives us a lightweight settings manager, and we can install Compiz and the decorator of your choice on that, grab Compiz Boxmenu for the right-click pipe menu, and keep Nitrogen for the wallpaper and pcman-fm (or Thunar if you'd prefer it) for the file manager.

I guess [this guy]("http://crunchbanglinux.org/forums/topic/2827/howto-run-compiz-as-a-standalone-window-manager/") really did start from Ubuntu rather than Crunchbang, too, so it's fairly misleading. I do find it weird that there are so very many things that we can't seem to install in Crunchbang.

Oh, on Nautilus: it only draws a desktop if your gconf settings tell it to do so, and you don't have gconf settings under Crunchbang at all. With those settings changed, it's the same on my machine (Nautilus does not try to draw a desktop or continue run in the background when closed.)
I can't find Compiz Boxmenu anywhere, except for the sourceforge page. Any idea how to compile this tarball? The readme says it has to be installed to /usr/ because of a bug or something.

---

### Post by afrodeity on 2011-04-15
> **~Plue said:**
> theres cairo-compmgr. it could do menu/window animations, add shadows, and a flashy application switcher,etc....(and it seems smoother than xcompmgr)

//btw, no cube or wobbly windows

anyone succeed installing cairo-compmgr? Having trouble with dependencies
```

libcairo-compmgr0:
 Depends: libvala0 (>=0.7.10) but it is not installable
```

libvala-0.10-0 is installed and libvala-0.12-0 is available in repos, but no libvala0

---

### Post by ~Plue on 2011-04-15
> **afrodeity said:**
> anyone succeed installing cairo-compmgr? Having trouble with dependencies
```

libcairo-compmgr0:
 Depends: libvala0 (>=0.7.10) but it is not installable
```libvala-0.10-0 is installed and libvala-0.12-0 is available in repos, but no libvala0
deb packages here >> [https://launchpad.net/ubuntu/maverick/+package/libvala0](https://launchpad.net/ubuntu/maverick/+package/libvala0)

---

### Post by Copper Bezel on 2011-04-15
XsheepX, /usr/ is the default location, and the readme was simply indicating that trying to override the default location breaks the application for some reason. The make process requires libdbus-glib-1-dev along with (of course) build-essential, but after fetching it, cd-ing into the appropriate directory and running make and sudo make install worked all easy-like.

Edit: Fifteenth or so: It's not a bad little menu. The right-click isn't working for me yet, but I think there's a configuration issue. It has task and viewport switching, a reasonable amount of configurability, recent documents. The readme becomes vitally important in setting it up, though. = )

Edit ... *again*. = ) I found a trick for a smoother login: put a & sleep n; between startup items, where n is the number of seconds you actually expect the app to take to load. I get a much smoother, faster, more reassuringly progressive login, and it fixed the fabled "Compiz wallpaper in 10.10" bug, along with some other problems with my startup apps.

---

### Post by Version Dependency on 2011-04-16
> **Copper Bezel said:**
> XsheepX, /usr/ is the default location, and the readme was simply indicating that trying to override the default location breaks the application for some reason. The make process requires libdbus-glib-1-dev along with (of course) build-essential, but after fetching it, cd-ing into the appropriate directory and running make and sudo make install worked all easy-like.

Edit: Fifteenth or so: It's not a bad little menu. The right-click isn't working for me yet, but I think there's a configuration issue. It has task and viewport switching, a reasonable amount of configurability, recent documents. The readme becomes vitally important in setting it up, though. = )

Edit ... *again*. = ) I found a trick for a smoother login: put a & sleep n; between startup items, where n is the number of seconds you actually expect the app to take to load. I get a much smoother, faster, more reassuringly progressive login, and it fixed the fabled "Compiz wallpaper in 10.10" bug, along with some other problems with my startup apps.


For those trying to get compiz-boxmenu to work properly, the README instructions contain an error if you are installing this on a recent version of Ubuntu:

```
Viewport Switcher > Desktop-based Viewport Switching > Plugin for initiate action to "core"
```

The above is wrong.  Instead of "core" you should put "commands".

---

### Post by Copper Bezel on 2011-04-16
Ah. Excellent. Thanks!

---

### Post by Copper Bezel on 2011-04-16
Not to bump, but I realized I should have posted my results. XsheepX, is this the sort of thing you're looking for?

[img]http://dl.dropbox.com/u/17749392/Screenshots/boxmenu.png[/img]

---

### Post by XsheepX on 2011-04-16
> **Copper Bezel said:**
> Not to bump, but I realized I should have posted my results. XsheepX, is this the sort of thing you're looking for?

[IMG]http://dl.dropbox.com/u/17749392/Screenshots/boxmenu.png[/IMG]
Yes, sir! Are you able to edit the menus, like Windows, viewports, etc.?

---

### Post by Copper Bezel on 2011-04-16
Yeppers. = ) Everything in the list either a submenu or an item, and you can put them wherever you want. Possible items include launchers for apps and places, the workspace and task selectors, recent documents, etc.

---

### Post by Version Dependency on 2011-04-17
> **Copper Bezel said:**
> Yeppers. = ) Everything in the list either a submenu or an item, and you can put them wherever you want. Possible items include launchers for apps and places, the workspace and task selectors, recent documents, etc.


I have a couple of pipemenus that I used in openbox that I've converted to work in compiz-boxmenu.  I figured I should post them here in case anyone needs them.

One is a date and time pipemenu. Below is the code to enter into the xml menu file.

```
<item type="launcher">
        <name>Date and Time</name>
        <command mode2="pipe">~/.config/compiz/boxmenu/date-menu.sh</command>
        <icon>appointment</icon>
    </item>
```And the other is an mpd (music player daemon) pipemenu.  The script uses Sonata and mpc...but you can make a few minor changes if you use other mpd clients instead.  Below is the code to enter into the xml menu file.

```
<item type="launcher">
        <command mode2="pipe">~/.config/compiz/boxmenu/mpcob.sh</command>
        <name>Music Player</name>
        <icon>radio</icon>
    </item>
```Attached are the pipemenu scripts.  I had plans to work on more but lately I've been using Unity so I haven't played around much with compiz standalone.  I know I eventually want to get a weather menu working but that's a bit bigger of a project.

---

