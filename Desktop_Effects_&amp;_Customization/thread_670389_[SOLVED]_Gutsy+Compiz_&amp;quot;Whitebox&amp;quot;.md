---
title: "[SOLVED] Gutsy+Compiz: &amp;quot;Whitebox&amp;quot; shadows"
date: 2008-01-17
forum: Desktop Effects &amp; Customization
---

### Post by eternicode on 2008-01-17
I just "upgraded" from Feisty via a fresh install.  Got compiz working, setup, [added a couple unstable plugins]("http://forum.compiz-fusion.org/showthread.php?t=5303"), and it works.  Except for one issue.

Some (well, most) of my drop shadows are showing up as opaque white boxes.  This affects the kicker panel (positioned at the top of the screen), tooltips, notifications, and menus.  The windows' drop shadows work fine, though :confused:

Currently enabled plugins, according to ccsm:

Accessibility: Enhanced Zoom

Desktop: Desktop Cube, Expo, Rotate Cube, Show Desktop

Effects: Animations, Cube Atlantis, Cube Reflection, Fading Windows (solely for visual bell), Window Decoration, Wobbly Windows

Extras: Screenshot, Screen Saver

Image Loading: JPEG, PNG, SVG, Text

Utility: Crash Handler, GLib (whatsit do??), iNotify, Regex Matching, Scale Addons, Video Playback

Window Management: Move WIndow, Place Windows, Ring Switcher, Scale, Shift Switcher

Uncategorized: Resize Window

Has anyone else experienced the white shadows?  Does anyone know which plugins might be causing it?

And I know the unstable plugins I added aren't the problem, because the shadows were the same before I added them.  I believe the shadows appeared the first time I started compiz; I was able to get them back to regular shadows once, but can't for the life of me figure out how :???:

Any help's appreciated!


EDIT:
I've also noticed that, occasionally, the window decorations will be partially missing

[ATTACH]56724[/ATTACH]

Resizing the window fixes this, though.  Changing "Shadow windows" in "Window Decoration" from "any" to "Normal" removes the offending boxes...but I'd rather have the nice shadows :)

---

### Post by lian1238 on 2008-01-17
Do you use emerald or just gtk?
If you're using emerald, try switching to gtk:
```
gtk-window-decorator --replace
```
Also, what theme are you using? I'm not sure if it's related to your problem.

Question: in your screenshot, is the whitebox shadow present?

---

### Post by eternicode on 2008-01-17
Currently I'm using kde-window-decorator (I'm using Kubuntu).  The window decorations are Crystal (from KControlCenter -> Appearance & Themes -> Window Decorations).

That snapshot was just the glitchy window decorations.  Here's one of the white boxes:

[ATTACH]56741[/ATTACH]

---

### Post by eternicode on 2008-01-18
Solved.  Well, worked-around, anyway.  The shadows are still solid white with kde-window-decorator, but I switched to gtk-window-decorator so I could use a Metacity theme that I like, and, voila, the shadows suddenly work :confused:

---

### Post by noirtier_de_villefort on 2008-04-01
my notifications (like a song name display on rhythmbox) appear as white boxes as well; i have no window decorations whatsoever... i've checked other threads, all containing advice like "change the defaultdepth to 24 in xorg.conf" and add:

Option "XAANoOffscreenPixmaps"
Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True"
Option "AllowGLXWithComposite" "true"

to my device section in xorg.conf. none of these changes have done anything... and none of the "(insert-window-decorator-here) --replace" commmands have worked. any help?

---

