---
title: "Openoffice very slow in XGL"
date: 2007-10-28
forum: Desktop Effects &amp; Customization
---

### Post by vides2012 on 2007-10-28
Hi!

I have Kubuntu 7.10 with XGL on ATI.When I start openoffice, it loads for a minute, every single icon is loaded in a couple of seconds,and the window is in fullscreen, so I can't see the panels, or even window decoration.Moreover when I try to click on something, that painfully slow loading starts again from icon to icon.

Can anyone help me?

---

### Post by vides2012 on 2007-10-28
Strange.When I start OO Writer, its all ok, but when I try to run spreadsheet,or draw, or any other OO, it is so slow.

Noone can help me? I've found nothing useful on google :(

---

### Post by vides2012 on 2007-10-29
noone's experiencing the same problem as me? :S

---

### Post by vides2012 on 2007-10-29
Well finally someone helped me:

bash -c "XLIB_SKIP_ARGB_VISUALS=1 oowriter"
bash -c "XLIB_SKIP_ARGB_VISUALS=1 oocalc"
bash -c "XLIB_SKIP_ARGB_VISUALS=1 oodraw"
bash -c "XLIB_SKIP_ARGB_VISUALS=1 ooimpress"
bash -c "XLIB_SKIP_ARGB_VISUALS=1 oobase"

after running these commands, they will work normally after running from simply the K menu.
Though oo still don't have a window decoration

---

