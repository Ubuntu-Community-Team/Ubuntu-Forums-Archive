---
title: "Screen issue after KVM installation."
date: 2015-09-27
forum: Desktop Environments
---

### Post by Stormlord on 2015-09-27
[COLOR=#141823][FONT=helvetica]Does anyone know how the following issue can be fixed please?
[/FONT][/COLOR]
[COLOR=#141823][FONT=helvetica]The system is Xubuntu 14.04 using XFCE 4.11 with two screens. The second screen has been placed to the right of the first using "Displays" in Settings.[/FONT][/COLOR]
[COLOR=#141823][FONT=helvetica]A few days ago, KVM had to be installed on that system and XFCE, or XFWM4, started behaving differently after that installation. Icons on the panel that needed to be right-clicked on, for their menus to appear now have to be left-clicked (screenlets manager icon for example), otherwise the plugin menu appears instead. Got no problem with that although I'd like to know what's responsible for the change.
[/FONT][/COLOR]
[COLOR=#141823][FONT=helvetica]The most serious problem that has appeared though, is the fact that although windows maximize properly on the left screen, they do not maximize properly on the right screen. They do resize properly by dragging their borders manually but the moment the maximize button is clicked, the window becomes smaller, leaving an empty space on the right side of the screen although there's nothing else there. Fullscreen video playback is ok on that screen and all manual window moves are ok. Only "maximize" does something wrong.

I'm giving some extra info just to avoid the corresponding suggestions because they have already been tested:
1. Workspace borders are manually set to 0 for all four sides.
2. Sometimes BUT NOT every time, when we log out and back in, the "maximize" problem is fixed.
3. As I've already stated, XFWM4 is used and not some other window manager, although compiz is installed too but it's inactive.
4. The system's graphics card is Intel therefore the open source driver is used and all configurations are made through XFCE's settings.
5. There are no panels on the right screen, thus, no hidden panel prevents proper maximizing.

It's obvious that KVM installed something that's interfering with window manager settings and I'd appreciate it if you could help on this.

Thanks again!
[/FONT][/COLOR]

---

