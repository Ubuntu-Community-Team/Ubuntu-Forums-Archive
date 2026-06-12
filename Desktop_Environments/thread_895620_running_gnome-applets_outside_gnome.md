---
title: "running gnome-applets outside gnome"
date: 2008-08-20
forum: Desktop Environments
---

### Post by apfergus on 2008-08-20
In a fit of summer boredom I decided to install Fluxbox on my laptop running Hardy. Turns out, I really like it with one small exception. While I can find numerous places on the internet eager to tell me how to make my Fluxbox desktop look amazing I cannot find a single one that will tell me how to do what I want to do.

I've managed to run the gnome wireless internet connection applet (nm-applet) at startup, but I'm still missing applets like volume control, laptop battery monitor, and the ability to put the computer in hibernate, restart, or shutdown without first exiting to the login screen. 

My hypothesis is that since I can run the one gnome applet, that I could probably run at least some of the others if only I had some way of knowing what they're called. My search-fu must be extraordinarily weak because I cannot find a single *list of default gnome-applets*, which seems like it should at least be available *somewhere*.

So if I could be directed toward a resource that will tell me how to get any of these things working in Fluxbox, whether it be through using the gnome applets already installed on my system or not, I'd really appreciate it.

---

### Post by CarlosNYB on 2008-08-20
I'll let you know what I come up with a little later -- busy today...

---

### Post by CarlosNYB on 2008-08-20
First of all check synapse to see what you find under dock apps or applets.

You might want to see if there is a Dock App that does the job from dockapps.org.  Fluxbox is supposed to work well with dockapps.

[http://dockapps.org/]("http://dockapps.org")

If you can't find what you want there, you can try Gnome files and see if the applets can be added just as they are with the network manager, in the startup file, although I'd want to stay away from too many gnome or other applets in fluxbox, myself.

[http://www.gnomefiles.org/](http://www.gnomefiles.org/)

I'd use these files to see what's available and then look in synaptic because repositories are a good thing.

---

### Post by apfergus on 2008-08-20
> You might want to see if there is a Dock App that does the job from dockapps.org. Fluxbox is supposed to work well with dockapps.

I've tried several dockapps and suspect from the results that I have no idea what I'm doing. All of the dockapps I've tried take the form of large, usually ugly, boxes which appear centered on the bottom of my desktop such that the Fluxbox slit will pop up and cover them should I move the cursor down to use them. Also, if I run more than one they all appear in the same place and cover each other up so I can only see one. As far as I can tell there is no way of moving them.

Ultimately what I'd like is something that just sits in the Fluxbox slit like the network manager does or like pidgin or liferea do when minimized, but if I can find an attractive looking dockapp I'll use it so long as I can put it in some location where it isn't incredibly obnoxious.

---

### Post by CarlosNYB on 2008-08-21
I'm hoping someone enlightens us, because what I'm getting is a largish box, not a docked app(let) on the task bar.

---

### Post by CarlosNYB on 2008-08-21
Also search this page for applets

[http://packages.ubuntu.com/hardy/gnome/](http://packages.ubuntu.com/hardy/gnome/)

---

### Post by ans5685 on 2008-08-22
> **apfergus said:**
> I've tried several dockapps and suspect from the results that I have no idea what I'm doing. All of the dockapps I've tried take the form of large, usually ugly, boxes which appear centered on the bottom of my desktop such that the [COLOR="Red"]Fluxbox slit[/COLOR] will pop up and cover them should I move the cursor down to use them. Also, if I run more than one they all appear in the same place and cover each other up so I can only see one. As far as I can tell there is no way of moving them.

Ultimately what I'd like is something that just sits in the Fluxbox slit like the network manager does or like pidgin or liferea do when minimized, but if I can find an attractive looking dockapp I'll use it so long as I can put it in some location where it isn't incredibly obnoxious.

Hmmm... Fluxbox gives you two things except the desktop 
1. The Taskbar-pager-system tray-clock 'bar' and 
2. The slit.
So the taskbar is NOT the slit :)
And all Dockapps go into the SLIT and not The Taskbar-pager-system tray-clock .
If you want the dockapps to be at any particular part of the desktop then right click on the  pager part of the Taskbar-pager-system tray-clock  and navigate to slit and placement and you can put it in ANY edge of the screen. What more you can auto-hide it or if you want, make it so that other apps can cover it.What more you should choose the orientation i.e. horizontal/vertical so that you don't have dockapps covering each other.:guitar:

---

### Post by maniheer on 2008-08-22
I think you got nm-applet working because it goes in the system tray. 

I hope I'm wrong :)

---

### Post by apfergus on 2008-08-22
> **ans5685 said:**
> 
And all Dockapps go into the SLIT and not The Taskbar-pager-system tray-clock .
If you want the dockapps to be at any particular part of the desktop then right click on the  pager part of the Taskbar-pager-system tray-clock  and navigate to slit and placement and you can put it in ANY edge of the screen. What more you can auto-hide it or if you want, make it so that other apps can cover it.What more you should choose the orientation i.e. horizontal/vertical so that you don't have dockapps covering each other.

Ahh. When I was reading through the fluxbox documentation it kept hammering on the fact that the slit was not the toolbar, so I kind of stupidly assumed that this meant the thing I thought should be called the tool bar must not be. Thanks for correcting me. 

Equipped with this knowledge, I have moved the slit to some more friendly part of my desktop (upper left corner) and installed wmix for volume control. I've got Conky running and displaying battery status in a way that is functional but not too attractive (I'm working on it), so I think I've nearly got everything I want at this point.

---

### Post by spupy on 2008-08-30
Start gnome-power-manager for a battery icon in the tray. You can click it and it can put your computer to sleep/hibernate.

---

### Post by CarlosNYB on 2008-08-31
Is that a dragon-ball-z smiley?

---

### Post by EnGorDiaz on 2008-08-31
what kind of apps are you trying to run just dock apps cus that site is as good as it gets

---

