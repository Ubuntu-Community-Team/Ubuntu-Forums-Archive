---
title: "Creating a custom DE"
date: 2015-08-21
forum: Desktop Environments
---

### Post by Igo361 on 2015-08-21
I couldn't figure out whether to post this thread here or in "General Help". My apologies if I made the wrong choice.

So typically I build up my everyday working environment from the netboot mini.iso, but I am never quite satisfied with the end result as I am stuck in a perpetual limbo between noob and linux-savvy; I usually wind up going with a stripped down XFCE (or LXDE) for 2 main reasons:


[LIST]
[*]a good pre-made applications ("start") menu, rather than the Debian menu most window managers will display by default, and 
[*]the ability to quickly and easily set auto-starting applications. 
[/LIST]

This thread will probably span several questions so let me ask the first two right now, is there a way to have whatever window manager display a good pre-made apps menu without having to install a panel? It'd be much more convenient to have a quick-launch and a systray by themselves than a full blown panel.

Also, is there something to set up auto-starting apps graphically or easily via text? bear in mind that "easily" is a relative term, as I'm sure a lot of you find LUA and all sorts of strange programming languages easy. When I say easy I mean as easy as if it were done via GUI.

Final question for the opening post, while on the topic of window managers, is there some form of TWM clone that's actively developed or has plans to be updated for xinerama, wayland/mir etc? TWM is excellent but I'd like to know I won't have to switch to a different WM in a few months/years... alternatively, any WM that:


[LIST]
[*]is ICCCM and EWMH compliant. 
[*]is just a WM (no built in panels or other stuff, I like to supply whatever's needed). 
[*]displays the apps menu by clicking on the desktop. 
[*]follows the mouse-pointer for focus. 
[*]raises windows via click. 
[*](if possible) allows the user to remove the "X" button and create a menu with close and kill functions. 
[*](if possible) displays a window list by clicking on the desktop. 
[/LIST]

I'd appreciate any hints or suggestions...

---

### Post by tea for one on 2015-08-23
Good evening

I had to find out via a web-search the meaning of the acronyms in your original post and here is what I have discovered:-

TWM                 Tab Window manager
ICCCM              Inter Client Communications Conventions Manual
EWMH               Extended Window manager Hints

I hope that somebody will offer advice soon but, I reckon that a question detailed with unfamiliar acronyms will not elicit suitable responses.

Anyway, here's my best shot; Openbox

---

### Post by Igo361 on 2015-08-24
Today I had a few minutes of spare time to do a bit of googling and reading. From what I understood, the sucky Debian menu most stand-alone window managers display by default when you right-click is based on "menu files" whereas the menu you see on XFCE or LXDE is based on .desktop files. Sources:

[http://debian-handbook.info/browse/stable/sect.customizing-graphical-interface.html](http://debian-handbook.info/browse/stable/sect.customizing-graphical-interface.html) (scroll to the bottom)
[http://wiki.debian.org/Proposals/DebianMenuUsingDesktopEntries](http://wiki.debian.org/Proposals/DebianMenuUsingDesktopEntries)

So knowing that (and assuming I understood correctly) is there any way to have, say, jwm, Openbox or whatever other WM display a .desktop file-based menu rather than the Debian menu?

---

### Post by tea for one on 2015-08-25
I suggest that you create a spare partition on your PC and install a test system with Openbox or JWM to ascertain if they are suitable for your needs.

Is this link via the Openbox site any help?

[http://openbox.org/wiki/Help:Getting_started#Using_Openbox_without_a_desktop_environment_.28The_lightweight_approach.29](http://openbox.org/wiki/Help:Getting_started#Using_Openbox_without_a_desktop_environment_.28The_lightweight_approach.29)

---

