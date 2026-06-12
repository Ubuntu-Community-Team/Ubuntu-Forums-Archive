---
title: "Independent workspaces for Gnome Shell and Unity"
date: 2011-12-21
forum: Desktop Environments
---

### Post by waynesherman on 2011-12-21
I have been researching different desktop environments over the past few weeks.  After testing KDE 4.5 plasma, I can really see the benefit of having customizable and independent workspaces/virtual desktops (they call them "[[COLOR=Blue]activities[/COLOR]]("http://maketecheasier.com/use-kde-plasma-activities/2010/09/01")").  They allow:

[LIST]
[*]Different wallpaper for each workspace
[*]Different desktop shortcuts for each workspace
[*]Different panels, widgets, and launchers for each workspace
[/LIST]
   Since I prefer the look and feel of Gnome and Unity, I have searched to see if they can be made to do the same thing.  I haven't found a solution yet (you can create different wallpapers per workspace, but you loose the desktop icons)

  Does anyone know if the same thing is currently possible in Gnome and/or Unity?

(I would also consider LXDE or XFCE if they can do it)

---

### Post by thaelim on 2011-12-21
Gnome 3 definitely can't do any of those. Unity can (AFAIK) do different wallpapers for each workspace (via Compiz tweaking), not sure about the others (there may be Compiz tweaks for them too, but I doubt it).

---

### Post by LewisTM on 2011-12-22
That's a challenge. I don't think there is any all-in-one solution for you.

Wallpapers: You can try Wallpapoz which will do that. It doesn't support Compiz though so no Unity 3D for you.

Desktops: There is only one ~/Desktop directory so having multiple ones would require some scripting or the ability to mask  items depending on the workspace. Since the icon placements are stored elsewhere and managed by the desktop manager, it should be possible if someone is willing to code it.

Launchers/panels: I know Cairo-dock can set launchers and  desklets to appear only on a given workspace. Entire panels too but I was unable to make that work.

If you really want to separate the workspaces for different tasks and apps, you could also create several users, each with their personal setups, and quickly switch between them.

Cheers!

---

