---
title: "Panel Float Above Maximized Windows"
date: 2008-04-15
forum: Desktop Effects &amp; Customization
---

### Post by Kiri on 2008-04-15
Is there any way I can get windows to maximize to the full screen size without being defined by the limits in place by the panel?

I actually want to have a floating panel (non-expanded) which will sit at the top of the sceen and over the title bar of maximized windows. I can get the panel to float, but when it is at the top of the screen it automatically makes that top area off limits to windows and desktop icons...

---

### Post by Zorael on 2008-04-16
Tagging for interest, would also like to know how to set up a custom desktop area.

Perhaps it can be done in Compiz, when defining screen "resolution"? Such as, 1280+1024+0+**20**?

---

### Post by Kiri on 2008-04-17
It seems like either it is not possible, or no one knows how to do it... :(

@Zorael: I see you use KDE? Is it possible to do this with the panel in KDE then?

---

### Post by Zorael on 2008-04-17
I believe the KDE Kicker panel is always expanded (or hidden), and that you can't make it "float".

Is there an 'always beneath' option available in its properties? Perhaps you could pick that, and then in Compiz/other window manager set it up to always make it show on top. That way, the inner mechanics would make it not limit the desktop area while Compiz would force it to go on top of everything. Hopefully.

---

### Post by Kiri on 2008-04-17
Thats a good idea. But I don't know how I can make compiz do that to a panel. For an application yes, but I don't know about the panel...
And actually I don't think there is an always beneath anyway :(

---

### Post by Zorael on 2008-04-17
Googling around, I seem to have found [some evidence](http://mail.gnome.org/archives/desktop-devel-list/2007-August/msg00102.html) suggesting it has being added to a later version/build. Perhaps the [Hardy version of it](http://packages.ubuntu.com/hardy/gnome-panel) has it? It might be troublesome to install though, if you need to upgrade the dependencies as well. Perhaps if you added the Hardy repositories or downloaded a Live CD (and then added the CD as a software source), then *only* upgrading gnome-panel, and then removing the software source.

To be sure (and if you have the time to spare), try downloading a Live CD of the Ubuntu flavor, run it and see if the option exists.

As for the Compiz setting, you want to muck about in the Window Rules plugin. Delve information from the panel by opening a terminal and running **xwininfo**, then clicking on the panel itself.
```
$ xwininfo
```
How to define the panel as a "window" that should always be on top (once you know its true title or its class) in the Rules plugin [is detailed in this wiki post](http://wiki.compiz-fusion.org/WindowMatching).

---

### Post by Kiri on 2008-04-18
Hey Zorael, thanks for all that.
I'm actually running Hardy 8.04 already, but there is no option like that for the panel, even in gconf editor :(

I sent an email to the guy who got the always beneath thing going though, so hopefully he will give me some ideas..

---

