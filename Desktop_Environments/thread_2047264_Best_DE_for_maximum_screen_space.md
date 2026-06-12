---
title: "Best DE for maximum screen space?"
date: 2012-08-24
forum: Desktop Environments
---

### Post by XrRydr on 2012-08-24
I got a new laptop and I've been trying a lot of different distros to see which fits.  What I'm curious about is how to maximize screen space.  I'm thinking the best way is to eliminate any sort of panel or bar at the top or bottom.  I suppose all I need on a panel is a clock, volume button, wireless button, and a battery monitor.  As long as the DE has some sort of application launcher and a way to check on time/wireless/battery without hassle, I think it'd be fun to try.  

I tried unity and didn't quite like it, hiding the dock didn't quite work well, it was really finicky and didn't hide correctly most of the time.  The top bar implementation was off from the mac version, I didn't like that to see the File,view,edit, ect. I had to hover over it and it wasn't always visible.  

Gnome3 might fit this with extensions, I haven't spent enough time on it.

I am also curious about openbox/fluxbox/otherboxes.  That window manager only approach is new to me, but I'm interested to see how that works.  Anybody have success with those?

---

### Post by Lisiano on 2012-08-24
You could try KDE.
You can disable all panels and put launchers, clocks, systray on the desktop.

EDIT: By default, you can see all widgets/plasmoids that are placed on the desktop by pressing Ctrl+F12. You can interact with the widgets in that mode too.

---

### Post by m_duck on 2012-08-24
To start with, Gnome 3 is probably quite a good choice since generally, there is only the top bar visible with those things you want. By default, the window frames are pretty chunky, but can be changed (IIRC).

Box-wise, if you don't mind spending some time setting them up they will be a good choice. I'm currently using PekWM (but am primarily an Openbox user). You can set up your right click menu to show the information you want, or have it in Conky (system monitor extraordinaire!) for example.

I typically use the window managers without a panel so usually go for the clock in Conky (or just run *date* in the terminal...

The downside of the *boxes etc. on a laptop (in my opinion) is that they can be quite mouse-centric out of the box compared to, say, Gnome 3. That said, they are all *very* configurable in terms of keybinds and mousebinds (probably PekWM more, and overwhelmingly so at times). You can set up binds to open programs, move them across desktops, change their position on a desktop, shade, minimise etc.

I have attached my PekWM set up to clarify my description above, though note it is pretty bare at the moment as I only reinstalled my machine on Wednesday, so haven't finished setting up yet!

EDIT: Sorry for the poor screenshot quality, I guess UF compresses attachments - I will upload a better one later if needed / I remember.

---

### Post by vasa1 on 2012-08-24
When OP wants "maximum screen space" what does it mean? Does it mean that the current app should occupy most of the screen? If so, then how does having stuff such as indicators or clocks on the desktop serve the purpose?

---

### Post by cortman on 2012-08-24
The DE that will allow you to do the most as far as configuration is Enlightenment. The only standard part of Enlightenment is the left click on desktop menu feature. Nothing else is unalterable, and it provides great GUI's for most editing.
If you want to try Enlightenment I'd suggest trying Bodhi Linux, which is Ubuntu based.

---

### Post by XrRydr on 2012-08-24
Yes, I do want the current app to occupy all of the screen.  What I'd be looking for is a desktop where the app can occupy all of the screen, but where I can have quick access to clock and indicators, perhaps with a toggle button.

---

### Post by papibe on 2012-08-24
Hi XrRydr.

If you want to try an absolute minimalistic DE, take a look at xmonad. No bars, no decorations. Note that it takes some time to get used to it.

This is the project [home]("http://xmonad.org/"), and this is how it [works]("http://xmonad.org/tour.html").

Regards.

BTW, it is on the repositories.

---

### Post by mparillo on 2012-08-24
> **Lisiano said:**
> You could try KDE.
You can disable all panels and put launchers, clocks, systray on the desktop.

EDIT: By default, you can see all widgets/plasmoids that are placed on the desktop by pressing Ctrl+F12. You can interact with the widgets in that mode too.

KDE is nicely customizable that way, but for quick and dirty, out of the box, Kubuntu recognizes that my netbook is best served by the [Plasma Netbook Workspace]("orkspaces/plasmanetbook/"), which is pretty space-efficient.

---

### Post by ajgreeny on 2012-08-24
Whatever DE I have used I have always had only a single panel at most, and kept that sized down to about 24 pixels.  That way I have never used too much of the screen estate for things that are not needed to be seen all the time.
The attached screenshot shows my 10.04, gnome2, bottom (and only) panel with (from L -R)
MainMenu, Home, Workspace switcher, Window List,
Empty space, then over to the right side.
Disk Mounter, Network Monitor, Terminal launcher, Libreoffice launcher, Stardict, Link to txt file, Tracker icon, Skype, Gmail-notify, HPLIP Toolbox, Parcellite, Network manager, Volume, Trash, Clock with weather, Synaptic launcher, Shutdown.

This gives me the things that I use a great deal with just a single click, and as you can see takes very little space.  I don't like and don't use unity at all, so in my 12.04 Ubuntu I use the gnome-panel classic DE, in which I have almost the same panel layout and applets.

---

### Post by m_duck on 2012-08-24
> **vasa1 said:**
> When OP wants "maximum screen space" what does it mean? Does it mean that the current app should occupy most of the screen? If so, then how does having stuff such as indicators or clocks on the desktop serve the purpose?
What I was getting at is that if you want the information there it can reside on the desktop and a keybind could be used to show/hide everything. In that scenario, all space is left for the programs being used.

I guess for most efficient use of space a tiler would probably be best but that takes some getting used to.

---

### Post by vasa1 on 2012-08-24
> **XrRydr said:**
> Yes, I do want the current app to occupy all of the screen.  What I'd be looking for is a desktop where the app can occupy all of the screen, but where I can have quick access to clock and indicators, perhaps with a toggle button.

Someone had asked something similar for Xfce ... about not having any panel at all. If I find what I think I remember, I'll post that link.

BTW, I really need the System Load Indicator and Psensor things to be **always visible**. I'm not happy with toggling to find that something has been hogging CPU behind my back.

---

### Post by Jakin on 2012-08-24
I noticed KDE4 (desktop) doesn't really have a limit as to how thin you can make panels, however Gnome panels can only shrink so much.

So you'd have one super thin bar with tasks, indicators, and start/app launch- the rest of the screen, well, that's all upto you :)

EDIT: Also, you could just auto hide the panel in most DE, so that would leave the entire screen, and the panel would only be visible when you absolutely need. KDE4 auto hide is quite smooth, it with hover over the window like a drop down menu.

---

### Post by black veils on 2012-08-25
I think xfce would be best, it's easy to use and has plenty of configuration options. you can have a panel and set it to auto-hide, also there is an option to hide window decorations when apps are maximized.

---

### Post by Buntu Bunny on 2012-08-25
> **black veils said:**
> I think xfce would be best, it's easy to use and has plenty of configuration options. you can have a panel and set it to auto-hide, also there is an option to hide window decorations when apps are maximized.

I was thinking Xfce too, but have been interested in other responses. I learned about a few new DEs today.

---

### Post by neu5eeCh on 2012-08-25
I asked myself this same question about a year ago. 

I finally settled on XFCE. I find that you can make XFCE use screen space more efficiently than any other DE. I don't know about Enlightenment. It's possible that Enlightenment is _as_ efficient.

In XFCE, you can bind any key to maximize any app (eliminating all panels and window decorations) -- a slightly different function than F11. In Firefox, for example, maximizing the app (in XFCE) will _retain_ your tabs (because it is only eliminating the panel and window decorations), whereas using F11 will _hide_ your tabs.

Also, if you want to keep your panel visible but hide the window decorations, this is accomplished via the following:

> Copy and paste this into your favourite text editor:

----

#! /usr/bin/python
from gtk.gdk import *

w=window_foreign_new((get_default_root_window().property_get("_NET_ACTIVE_WINDOW")[2][0]))
state = w.property_get("_NET_WM_STATE")[2]
maximized='_NET_WM_STATE_MAXIMIZED_HORZ' in state and '_NET_WM_STATE_MAXIMIZED_VERT' in state
if maximized: w.unmaximize()
if w.get_decorations() == 0 :
    w.set_decorations(DECOR_ALL)
else:
    w.set_decorations(0)

if maximized: w.maximize()
window_process_all_updates()

----

Save in your home folder with the name decoration.pyI have bound this script to ctrl+spacebar. This means I can maximize an app window and still see the XFCE panel. With Firefox, this gives me more efficient usage of the screen than with Unity.

LXDE has the same functionality _built-in_, but lacks some of XFCE's other refinements.

If you like a Gnome base, you can try installing the Cairo Dock Session. This will give you a desktop with no panels and the dock can be set to hide. I had two problems with Cairo Dock session: 1.) It was buggy and unstable 2.) I never really cottoned to hiding docks and panels. XFCE allows me to see or hide the panel with one keyboard shortcut and the panel does everything the dock does without all the distracting eye-candy and buggy behavior.

I would **not** recommend Gnome. It is **not** designed to maximize screenspace without an ugly fight. Gnome devs did **not** design Gnome Shell to be customizable. You can install maximus to obtain a similar effect to the script offered above, but maximus is a PTA and not as flexible (opens all windows, no matter how trivial, full screen).

**Edit: **Forgot to mention: XFCE is modular. If you don't like the panel, you can delete it. Period. Then substitute Openbox, a dock, or nothing at all.

---

### Post by kevinmchapman on 2012-08-26
Yes, E17 does all that.

You can do everything you need with almost any DE or WM, so I wouldn't get too hung up on it. Just tweak what you are happiest with.

If you don't want a panel, or are happy with an autohide panel, then everything but Unity and Gnome are good. If you need a panel, Gnome can join the party. Gnome-Shell can happily run windows full-screen without decorations. Not sure about the comments above, as it **was** designed to do exactly this.

---

### Post by kio_http on 2012-08-26
> **mparillo said:**
> KDE is nicely customizable that way, but for quick and dirty, out of the box, Kubuntu recognizes that my netbook is best served by the [Plasma Netbook Workspace]("orkspaces/plasmanetbook/"), which is pretty space-efficient.

Agreed, also you can basically turn it into anything you want. E.g myself I prefer the desktop workspace on a netbook.

---

### Post by ActionpackedPIVII on 2012-08-26
I would say a tiling window manager like Xmonad or Awesome. If you want to focus on your current tasks and nothing else, they are really the way to go

---

### Post by Hylas de Niall on 2012-08-26
Why not just XFCE or LXDE with the panel(s) set to auto-hide?

Easy.

---

### Post by vasa1 on 2012-08-26
> **Hylas de Niall said:**
> Why not just XFCE or LXDE with the panel(s) set to auto-hide?

Easy.
Mine set to autohide with Xfce ...

---

### Post by markbl on 2012-08-26
> **Hylas de Niall said:**
> Why not just XFCE or LXDE with the panel(s) set to auto-hide?

Easy.
Why not the Unity (the default Ubuntu desktop) with the launcher set to auto-hide? Unity uses a global menu which is arguably most efficient on screen real-estate.

I prefer gnome-shell on my small-screen laptop. Simple, but also just works the best.

---

### Post by vasa1 on 2012-08-26
> **markbl said:**
> Why not the Unity (the default Ubuntu desktop) with the launcher set to auto-hide? Unity uses a global menu which is arguably most efficient on screen real-estate.

I prefer gnome-shell on my small-screen laptop. Simple, but also just works the best.
OP answers "why not Unity" in the first post.

---

