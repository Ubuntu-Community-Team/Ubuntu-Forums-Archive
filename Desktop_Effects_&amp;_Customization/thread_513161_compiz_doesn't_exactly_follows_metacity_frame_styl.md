---
title: "compiz doesn't exactly follows metacity frame style"
date: 2007-07-30
forum: Desktop Effects &amp; Customization
---

### Post by stido on 2007-07-30
Hi!

i've noticed this since a couple of weeks ago when i was using Gimp, and i'm not sure if this is a feature, a workaround, a bug, or a "not-yet-implemented":

as we all know, metacity can draw different frame style set for each window types (normal, utility, dialog, modal-dialog) as long as we define separate style sets for them in the theme's xml file. i love this feature.

now, compiz apparently doesn't follow metacity's style sets exactly as it is defined in the xml. all titlebars are drawn according to the Normal window frame style sets regardless. Compiz only omits certain buttons (minimize, maximize) if the window is a dialog or a utility palette.

when i turn off compositing and use plain vanilla metacity, the problem goes away. When i use beryl with metacity, the problem also goes away. so apparently only compiz who is not communicating very well with metacity.

to reproduce that:
try clearlooks window-border theme in metacity with compositing disabled (compiz/fusion, beryl, all off) and open up Gimp. The palette docks and toolbox windows now have non-rounded titlebar edges, and smaller window titles. 
After that, try the same in compiz with metacity decorations and compare the results.

so, kind friendly people, how do i fix this? :)

---

