---
title: "Changing window button size on xfce4-panel"
date: 2011-12-10
forum: Desktop Environments
---

### Post by cloud2dream on 2011-12-10
Hi all
Hoping some XFCE guru can help me here:

I'm trying to customize XFCE 4.8's panel so that the window buttons on the panel have no labels but are a bit wider than just the icon (50ish pixels or so). The settings menu on the panel only seems to offer the 2 extremes, not a specific width setting.

Is there a way to do this, maybe a config file somewhere? I'm using Xubuntu 11.10 but if it can be done on another distro I'd be happy to switch.

Thanks

---

### Post by ohnonot on 2012-02-11
i would be interested in this, too!
*bump*

---

### Post by Toz on 2012-02-11
You can configure the Window Buttons applet to not display labels by either:
1. Right-click on the windows button applet (try right-clicking just to the right of the last button) and selecting properties (from the "Window Buttons" menu) _OR_
2. Right-click somewhere on the panel, select Panel->Panel Preferences->Items tab, selecting Window Buttons and clicking on the "Edit" button.

When you get to the Window Buttons configuration dialog, uncheck "Show button labels".

The size of the icons is not directly configureable, but if you change the size of the panel itself, the size of the icons will change.

---

### Post by ohnonot on 2012-02-13
thanks toz,
but as far as i understand th op, we want to specify the (max.) width of the window buttons. which is not an option in the properties gui.
at least that's what i'd like to do :-)

---

### Post by ohnonot on 2012-05-05
i found it. 
add this to ~/.gtkrc-2.0:

style "xfce-tasklist-style"
{

  # The maximum length of a button before the label ellipsizes.
  # When this value is set to -1 the button will expand to the
  # entire available space.
  XfceTasklist::max-button-length = 50 # pixels. or whatever size you like
 
}
class "XfceTasklist" style "xfce-tasklist-style"

---

