---
title: "Is there any good dock that works with xcompmgr?"
date: 2007-08-14
forum: Desktop Effects &amp; Customization
---

### Post by picpak on 2007-08-14
My computer is too slow for Compiz-Fusion...sad, I know, but it can handle xcompmgr. The docks, however, do not.

AWN: Seems to be the de facto standard around here...not that it works or anything. Xcompmgr or not, it didn't make a difference, it still had no transparency and looked awful.
Gnome-dock: Even without transparency I thought this one was nice...but still, black background.
Gdesklets Starter Bar - looked pretty boring, but it didn't work either. Still a black background.
Kiba-dock: Haven't tried this one in a while, but last time I did it didn't work.
SimDock: Works perfectly...but no transparency, only a background image. Oh, and it doesn't load on all workspaces.
Adesklets YAB: Works perfectly, but a little bland. I'd like something a little more bling-y, if you will.

I know xcompmgr transparency works, I use it with Audacious XOSD. These docks won't use it though...any ideas/suggestions?

---

### Post by b3n87 on 2007-08-14
not sure what you meant there with AWN but i found that one the best

its very customizable to and its had transparency from the beginning
its move to launchpad now and its updated almost every other day now


give it a shot see what you think?

---

### Post by fabounet on 2007-08-14
Take a look at Cairo-Dock ;-)
[very short video]("http://www.youtube.com/watch?v=4qIdL79rqlo")
[ScreenCapture]("http://fabounet03.free.fr/Bureau02.png")

Light, numerous animations, easily customizable, works fine with xcompmgr, evolves quickly.

[The french Ubuntu forum page]("http://doc.ubuntu-fr.org/gnome_dock") about it, to see how to install the packages.

---

### Post by hyperair on 2007-08-14
Last I checked, all those docks require is a Compositing Manager, because they use Compositing to get the "true" transparency. If they don't run under xcompmgr, then your computer is obviously not running it properly, or you're not even running xcompmgr at all.

---

### Post by fabounet on 2007-08-14
?
of course it requires a composite manager.
Xcompmgr is one of them (the lightest of all)
where si the problem ? composite is great, the dock never goes over 2% CPU.

---

### Post by picpak on 2007-08-14
> **hyperair said:**
> Last I checked, all those docks require is a Compositing Manager, because they use Compositing to get the "true" transparency. If they don't run under xcompmgr, then your computer is obviously not running it properly, or you're not even running xcompmgr at all.

I'm pretty sure I'm running it when my windows have drop shadows. I thought maybe it was because I was using Openbox, but IceWM does the exact same thing.

Isn't Cairo-Dock the same thing as Gnome-Dock?

---

### Post by picpak on 2007-08-14
Well hot dog, I've solved it! The magic is with using xcompmgr with the -n switch. Thanks everyone!

---

### Post by fabounet on 2007-08-15
gnome-dock is the original one, it started and ended last year.
Cairo-dock is a completely new version made from gnome-dock, only the concept has remained unchanged.

---

