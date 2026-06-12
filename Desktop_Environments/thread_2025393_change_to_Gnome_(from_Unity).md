---
title: "change to Gnome (from Unity)"
date: 2012-07-14
forum: Desktop Environments
---

### Post by goodbye-windows(tm) on 2012-07-14
Hi All,

I tried Unity, it's ok....but my old Pentium 4 processor can't run Unity well. With no apps running and from a fresh boot, the processor load varies from 20% to 25%. As soon as I open the browser, with 2 tabs open, the processor load averages 50% (with gmail in one tab and this forum in the other).

I need a lighter weight desktop environment.

I think I'd like to try Gnome. Many users mention 'Gnome shell'. With Gnome running in a shell, doesn't that mean that the processor still sees Unity running with the additional load of Gnome?

How do I delete Unity (for good) and change to Gnome?

TY.

Art

---

### Post by orange2k on 2012-07-14
Gnome-shell doesn't run on top of Unity, it has its own redering engine - mutter, and it doesn't use Compiz.

You may try gnome-shell (gnome 3 if you wish), and see if it runs any better than Unity...

Personally, I prefer gnome-shell over Unity...

---

### Post by robtygart on 2012-07-14
> **goodbye-windows(tm) said:**
> Hi All,

I tried Unity, it's ok....but my old Pentium 4 processor can't run Unity well. With no apps running and from a fresh boot, the processor load varies from 20% to 25%. As soon as I open the browser, with 2 tabs open, the processor load averages 50% (with gmail in one tab and this forum in the other).

I need a lighter weight desktop environment.

I think I'd like to try Gnome. Many users mention 'Gnome shell'. With Gnome running in a shell, doesn't that mean that the processor still sees Unity running with the additional load of Gnome?

How do I delete Unity (for good) and change to Gnome?

TY.

Art

I have been thiking about doing the same. I was lookng at this. 
[http://ubuntuforums.org/showthread.php?t=2018617&highlight=gnome-classic](http://ubuntuforums.org/showthread.php?t=2018617&highlight=gnome-classic)

What do you think?

---

### Post by goodbye-windows(tm) on 2012-07-14
robtygart,

I guess I have to ask what the difference between Gnome Classic and the current version of Gnome....

What is the difference between Gnome and Gnome classic? Which has a lighter processor load (overhead)?

Currently, I'm running xfce and unity, on 2 different harddrives (same P4 processor punchbox). Xfce is fine, but it not quite as deluxe as I'd like to see. 

Gnome or Gnome classic?

TY

Art

---

### Post by robtygart on 2012-07-14
> **goodbye-windows(tm) said:**
> robtygart,

I guess i have to ask what the difference between Gnome Classic and the current version of Gnome....

What is the difference between Gnome and Gnome classic? Which has a lighter processor load (overhead)?

Currently, I'm running xfce and unity, on 2 different harddrives (same P4 processor punchbox). Xfce is fine, but it not quite as deluxe as I'd like to see. 

Gnome or Gnome classic?

TY

Art

Unity is Gnome, so I think what me and you are looking for is 
Gnome-classic.

---

### Post by goodbye-windows(tm) on 2012-07-14
I tried the variants of Gnome, and mainly judged them on processor utilization with 2 browser windows open and only the system monitor running.

I think I could adapt to Gnome and they all use less system resources than the full blown unity does.

I think I'll switch back to xfce and continue running Xubuntu.

Xubuntu has a useless search utility though (called catfish), it will find files and folders, but you can't select them and delete them if needed. 

Regards,

Art

---

### Post by buckeyered80 on 2012-07-14
I think the latest stable version of Gnome 3 (Gnome-shell) is pretty lightweight. Gnome classic may be better for a P4. I would try both and see which one works better. Just select it from the log in screen; Gnome classic or Gnome. Personally, I like Gnome-shell the best and I think Ubuntu should have just stuck with Gnome.

---

### Post by LewisTM on 2012-07-14
> Xubuntu has a useless search utility though (called catfish), it will find files and folders, but you can't select them and delete them if needed. 
You can still install gnome-search-tool in Xfce. Catfish is good at finding stuff but I agree it doesn't let you do much with the results.

If you want to jazz up your Xubuntu you should install Cairo-Dock and Synapse. The new Xfce 4.10 is also nice and stable.

Cheers!

---

### Post by Shadius on 2012-07-14
I'd suggest you try GNOME Classic. My Windows XP computer was having a hard time running Ubuntu with Unity so I switched to GNOME Classic and it runs a lot better. If you want to go even lighter, you can try Lubuntu or use the LXDE, even though I find LXDE to be uglier than the full Lubuntu package.

---

### Post by glennric on 2012-07-15
There seems to be a lot of confusion here as to what gnome, gnome-shell, gnome classic, and unity are.  Gnome is the desktop manager that ubuntu uses by default.  Gnome-shell, gnome classic, and unity are all different gnome sessions.  They just use different components of gnome and alternate window managers to give different user interfaces.

Gnome-shell is the true gnome 3.  It provides the windows manager (mutter) and the whole desktop gui.

Gnome classic and unity both run in the gnome 2 fallback mode of gnome 3.  Gnome classic uses the gnome-panel and is most like the old gnome 2.  Unity is Ubuntu's home brewed variant.  With both gnome classic and unity you have a choice of using compiz (and all the snazzy eye candy effects) or metacity for the window manager.

The most light weight version of all of those is to run the gnome classic session without effects (i.e. without compiz).  If you run gnome-shell, gnome classic with effects, or unity-3d then you have the added load of a compositing window manager.

That being said, low end computers will benefit from a desktop that has an even smaller resource footprint.  XFCE is better for this.  I don't know much about LXDE, but it is supposed to be made for low end computers.  So these are probably your best bet.  That is unless you want to forgo the GUI completely and go command line only.

---

### Post by Shadius on 2012-07-15
> **glennric said:**
> There seems to be a lot of confusion here as to what gnome, gnome-shell, gnome classic, and unity are.  Gnome is the desktop manager that ubuntu uses by default.  Gnome-shell, gnome classic, and unity are all different gnome sessions.  They just use different components of gnome and alternate window managers to give different user interfaces.

Gnome-shell is the true gnome 3.  It provides the windows manager (mutter) and the whole desktop gui.

Gnome classic and unity both run in the gnome 2 fallback mode of gnome 3.  Gnome classic uses the gnome-panel and is most like the old gnome 2.  Unity is Ubuntu's home brewed variant.  With both gnome classic and unity you have a choice of using compiz (and all the snazzy eye candy effects) or metacity for the window manager.

The most light weight version of all of those is to run the gnome classic session without effects (i.e. without compiz).  If you run gnome-shell, gnome classic with effects, or unity-3d then you have the added load of a compositing window manager.

That being said, low end computers will benefit from a desktop that has an even smaller resource footprint.  XFCE is better for this.  I don't know much about LXDE, but it is supposed to be made for low end computers.  So these are probably your best bet.  That is unless you want to forgo the GUI completely and go command line only.

Very nice explanation. That should clear up any confusion. Certainly helped me understand better.

---

### Post by kansasnoob on 2012-07-15
> **goodbye-windows(tm) said:**
> Hi All,

I tried Unity, it's ok....but my old Pentium 4 processor can't run Unity well. With no apps running and from a fresh boot, the processor load varies from 20% to 25%. As soon as I open the browser, with 2 tabs open, the processor load averages 50% (with gmail in one tab and this forum in the other).

**[COLOR="Red"]I need a lighter weight desktop environment.[/COLOR]**

I think I'd like to try Gnome. Many users mention 'Gnome shell'. With Gnome running in a shell, doesn't that mean that the processor still sees Unity running with the additional load of Gnome?

How do I delete Unity (for good) and change to Gnome?

TY.

Art

This setup runs well for me on as little as a 1100MHz CPU w/1GB of Ram:

[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370)

But you must use the Gnome classic (no effects) session which uses the Metacity window manager! Regular gnome classic uses Compiz!

If you need something lighter than that I'd look at Lubuntu.

---

### Post by Murdoc_of_puts on 2012-08-10
Hey I was wondering if anyone knew of a way to change things in gnome(not clasic).  There are a lot of things that I like in the new desktop, but there are also a lot of things I hate. Like no drop down main menu, not being able to add/move things on the panel, not having a desktop switcher on the panel.  I do like the anotated window selector though, it's a nice touch.  I'm not even giong into Compiz, I all ready know there's manuals worth of stuff for that.  I'm not really worried about CPU usage, but usage in general I am worried about.  So does anyone know how to fix those things?  Also, In G-classic you could change all of the winow manager things, but it doesn't even seem that you can change colors for this, so any help on these little tweaks would be appricated.

---

### Post by markbl on 2012-08-10
> **Murdoc_of_puts said:**
> Hey I was wondering if anyone knew of a way to change things in gnome(not clasic).
Log in to gnome-shell and then go to [http://extensions.gnome.org](http://extensions.gnome.org) and spent time experimenting with the many extensions there.

IMHO, we have all spent the last many years using a classic taskbar based DE so nearly all of us come to gnome shell and then immediately want to bend gnome shell backwards towards our familiar classic environment, which after applying many extensions is almost possible. That is just human nature. You don't need extensions however. Spend a lot of time in gnome shell and think carefully about why they have changed the things they have and you will come to appreciate the beautiful simplicity of the new way to do things.

---

### Post by vexorian on 2012-08-10
> **goodbye-windows(tm) said:**
> Hi All,

I tried Unity, it's ok....but my old Pentium 4 processor can't run Unity well. With no apps running and from a fresh boot, the processor load varies from 20% to 25%. As soon as I open the browser, with 2 tabs open, the processor load averages 50% (with gmail in one tab and this forum in the other).

I need a lighter weight desktop environment.

I think I'd like to try Gnome. Many users mention 'Gnome shell'. With Gnome running in a shell, doesn't that mean that the processor still sees Unity running with the additional load of Gnome?

How do I delete Unity (for good) and change to Gnome?

TY.

Art


I doubt gnome-shell would improve things for you.

You can try run unity-2D if you like the interface style. If you do not like it. Try fallback/classic gnome or xfce or lubuntu.

---

### Post by Murdoc_of_puts on 2012-08-12
[QUOTE=markbl;12162147
Spend a lot of time in gnome shell and think carefully about why they have changed the things they have and you will come to appreciate the beautiful simplicity of the new way to do things.[/QUOTE]

I've tried, but I think that the extensions are the way to go.  Don't get me wrong, there are a lot of things that I like about the new interface.  It's just very annoying that everytime I switch desktops, which is a lot, I have to go through their interface instead of just clicking on a desktop.  Also waiting for the interface to load, and then looking through all of the programs is really not all that quick just to start a program when I could select it from a drop down menu in about 3 secs, as opposed to 20 with the interface.

---

### Post by markbl on 2012-08-12
> **Murdoc_of_puts said:**
> It's just very annoying that everytime I switch desktops, which is a lot, I have to go through their interface instead of just clicking on a desktop.
You mean "workspace" not "desktop"? If you switch workspaces frequently then by far the most efficient way is to use the keyboard shortcut ctrl+alt+up/down. This is true also for Unity.

> 
Also waiting for the interface to load, and then looking through all of the programs is really not all that quick just to start a program when I could select it from a drop down menu in about 3 secs, as opposed to 20 with the interface.
Not exactly sure what you mean here but if you are starting frequently used apps from the applications overview then you are just doing it wrong. You should add frequently used apps to your launcher, or start them via the dash + search. This is also true for Unity. Even in gnome 2, if you were starting frequently used apps from the unwield tree of menus you were doing it the slow way there also.

Anybody starting with Gnome Shell should spend 5 mins reading the [cheat sheat](https://live.gnome.org/GnomeShell/CheatSheet).

---

