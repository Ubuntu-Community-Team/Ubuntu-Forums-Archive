---
title: "Cannot stop Plasma Notes randomly dropping Notes on my desktop"
date: 2020-10-18
forum: Desktop Environments
---

### Post by terryjcoles on 2020-10-18
Hi,

Since the last time I upgraded I've been plagued by Plasma Notes randomly popping up on my desktop.  I frequently use middle-click to generate a double click and if my mouse happens to be a bit outside the Window a Note is dropped on the desktop (usually with the last item in the Clipboard in it).

I never use sticky notes (I rarely used the paper variety in the old days) so I don't need this functionality.  I know how to remove the unwanted Note, but I can't work out how to stop the Note being dropped in the first place.  Clicking on the 'Configure Notes' spanner icon simply allows me to choose a colour scheme or a keyboard shortcut; it doesn't allow me to remove the Widget from the machine or change the way it is invoked.  I rummaged around in the 'Add Widgets' Panel, but that only allows me to add new Widgets (as you would expect), but doesn't allow me to uninstall or disable them.

Is there a way to stop this?

---

### Post by terryjcoles on 2020-10-23
Answering myself.  My local LUG Group sorted it out.  There are several factors at play here.  First the problem doesn't occur if the Widgets are unlocked. However, the ability to lock the widgets has been removed from the version of Plasma in Kubuntu 20.04 (5.18.5).  Second it would appear that the widgets were installed as a meta-package in earlier versions of Plasma, but now it is a fully packed package.

The thing that fixes this though is that the middle mouse button-behaviour is set in two places; in KDE Settings and in the Desktop Behaviour Settings.  Removing '[COLOR=#000000]middle-click to generate a double click' from the [/COLOR]Desktop Behaviour Settings doesn't seem to affect anything else.

I'm not sure why there are two places to set this.

---

