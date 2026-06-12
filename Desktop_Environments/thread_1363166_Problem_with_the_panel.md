---
title: "Problem with the panel"
date: 2009-12-24
forum: Desktop Environments
---

### Post by pushkar_k on 2009-12-24
There is some problem with the panel in kubuntu which (panel) is at bottom position. Whenever window is opened or minimized its link is shown there. Somehow I closed something unknowingly from that panel and now minimized windows jst vanish . Other things on panel such as widgets , sound control etc. are still there but they are now moved to left just after kubuntu start menu. Does anyone know how to fix this and restore default settings for panel ?

---

### Post by gunksta on 2009-12-25
It sounds like you accidentally deleted your task manager.

First, to answer your question -- Here's how to restore your Plasma Desktop to the default settings. Open a terminal application (konsole) and enter:
```
rm kde/share/config/plas*
```

This should nuke all of your plasma (dekstop) setting and restore your desktop completely.

But, it's a rather heavy handed approach. I would instead, replace the Task Manager. Look at your bottom panel. In the right hand corner you should see a little half circle (look closely, it's in the right hand corner). If you hover over this with your mouse, it lights up. Click on this "cashew". As set of options will appear. One of these options is to install more widgets.

Install the Task Manager Widget. While still in "edit" mode, you can move around the widgets in your tool bar (You can't if you aren't in this special edit mode).

This should fix your problem.

---

