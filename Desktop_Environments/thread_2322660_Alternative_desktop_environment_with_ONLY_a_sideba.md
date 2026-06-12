---
title: "Alternative desktop environment with ONLY a sidebar (no top panel menu bar, please!)"
date: 2016-04-29
forum: Desktop Environments
---

### Post by rishav2 on 2016-04-29
Currently, I'm running on stock Ubuntu 16.04 LTS with the default Unity DE. The only visual changes I've made are using Unity & Gnome Tweak Tools.

My issue, as it were, is to do with the Unity menu bar / the panel across the top of the screen. I have quite limited screen estate on my laptop, especially vertically. As a result, I was looking for a way to auto-hide that panel since it isn't all that useful to me under most circumstances. I'm all about keyboard shortcuts when it comes to general access of programs and windows/workspace management.

However, a brief Google later, it seems as if that's not a viable possibility at this point in time... Which is pretty unfortunate given that a Mac OS with a similarly styled GUI handles this very option quite well; although, I'm aware of making direct comparisons between something like Apple Mac to Ubuntu's open source project is a bit of a stretch.

Putting that aside, I believe that, for once, Windows 10 has achieved the perfect balance with their vertical task bar as shown in the image attached below.

[ATTACH=CONFIG]268719[/ATTACH]

Some of its notable features include:
[LIST]
[*]Apps can be pinned by just their icons.
[*]Pinned icons act as app launchers.
[*]Pinned icons also house live instance(s) of the app within itself.
[*]Indicators display when an app is live, active or has multiple instances open.
[*]System toggles (volume, network), notifications area & date/time widgets are all packed away neatly along the bottom.
[*]Right-click context menus are available from each app icon to access their commonly used features or switch between live instances of the app.
[*]Keyboard shortcuts to access any of the apps (Super + #) which can: open a new instance of the app, minimize the active app session & switch between different instances of the app.
[/LIST]

Unity has almost all of these features, bar the presence of widgets at the bottom: hence the existence of the menu bar. It also doesn't support all of the aforementioned keyboard shortcuts but it's got the important ones. Ideally, I'd like a replica of the Windows task bar on Unity. Tabs on Google Chrome browser are a big reason towards hiding the top panel since it serves no real purpose other than to make it that much more annoying to change tabs using the mouse, however occasional as that is.

With the arrival of the option to move the Unity sidebar to the bottom of the screen, I'd hoped there'd be some way to auto-hide the top panel. Since that hasn't been the case, I've looked around for alternative DEs which maintain a close resemblance to Unity while ticking most of the feature checkboxes above. Xubuntu Xfce was one of the options I'd tried & made some good progress towards my target. Having re-positioned the menu bar along the side of the screen & installed [DockbarX]("https://github.com/TiZ-EX1/xfce4-dockbarx-plugin") to combine & group app icons, it was a lot closer to what I was looking for. Unfortunately, all keyboard shortcuts are hard-coded to open pre-selected apps. A whole host of other packages & dependencies are also needed to be installed to get anywhere near the usual functionality of Ubuntu in terms of compton/compiz compositor visuals for window management as well as tweaks like hot corners & such.

So my question... Does anyone know of a very similar DE to Unity with a majority of features from the list above that can also hide its menu bar? Cheers.

---

### Post by buzzingrobot on 2016-04-29
XFCE's panel(s) can be relocated to either side of the display, and have a dock-mode option. 

Believe MATE can be configured without any panels and using a dock like Plank or Dockey.

There are, I recall, Gnome extensions that hide its top panel until a mouseover.  Look also at the Dash-to-Dock extension and how it can be configured. 

Panels and docks are typically assumed to be difference creatures.  Some of the functionality may not be available without a panel. A more esoteric approach would be a tilable window manager like i3 which is built to rely on keyboard use.  Add in a dock and a panel and maybe you'd have something.

---

