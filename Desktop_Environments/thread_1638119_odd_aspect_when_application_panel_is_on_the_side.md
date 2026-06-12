---
title: "odd aspect when application panel is on the side"
date: 2010-12-05
forum: Desktop Environments
---

### Post by glósóli on 2010-12-05
Hi everyone!

since I have a laptop with quite a smallish screen (13.4") and with really narrow vertical resolution, I used in win to have the app bar on the side, so to benefit from a wider vertical area.
but in Ubuntu, this really looks ugly (see screenshot for better acknowledgment).
basically the panel is divided into many small 'bricks', and when the application is open (and selected), it looks fine.
but if another application is opened, then the button of the first unselected app looks again with these sort-of bricks...
can this be solved somehow?

many thanks!

---

### Post by JOHNNYG713 on 2010-12-05
The brick look is inherent of having the panel on the side, I suggest to achieve more vertical space, right click your top and or bottom panels, click "properties" and ether "resize" the bar or "auto hide" or "show hide buttons"! also right click side panel and "remove panel".

---

### Post by mcduck on 2010-12-05
> **glósóli said:**
> Hi everyone!

since I have a laptop with quite a smallish screen (13.4") and with really narrow vertical resolution, I used in win to have the app bar on the side, so to benefit from a wider vertical area.
but in Ubuntu, this really looks ugly (see screenshot for better acknowledgment).
basically the panel is divided into many small 'bricks', and when the application is open (and selected), it looks fine.
but if another application is opened, then the button of the first unselected app looks again with these sort-of bricks...
can this be solved somehow?

many thanks!

The problem is that the theme you are using has defined a background picture for the panel (and panel applets), and that only works for horizontal panels.

Gnome-panel itself is actually able to rotate (and scale) background images correctly to fit vertical & horizontal panels and different sizes, but that only works if you set the background image directly from the panel itself. Also the rotate/scale options are disabled by default (I have no idea why) but at least they can be enabled through gconf-editor.

So, to get the panel theme to work correctly you'll have to do three things:

1. Remove any panel theming from your current GTK theme. If you are lucky the theme you are using has a separate panel.rc file, in which case you can just rename or delete it. If not, you'll need to edit the main theme rc file itself and remove any panel-related stuff from it. (this is required because most themes define the background not only for the panel itself, but for all applets as well, and that *will* override whatever you set in the panel's options)

2. Set the desired background image in gnome-panel's options. You'll probably find one in somewhere in the GTK theme's directory. (If you have already set the panel to use a background image instead of the one from your GTK theme, you can actually just drag&drop any image to empty space in the panel to set it as the background image)

3. Launch gconf-editor, browse to *apps/panel/toplevels/*your_panel's_name*/background* and enable the *rotate*-option (and *fit* or *stretch*, if you need)

---

### Post by C1377 on 2010-12-11
I had this problem too.

The simplest solution is to change to a theme that doesn't use a gradient.

---

### Post by vangop on 2010-12-11
Nah, the problem is that you have a window list applet on a vertical panel, which is buggy and not working. There's a lot of bug reports around.
The only way is to use some replacement for gnome-panel like cairo-dock or AWN.

---

### Post by glósóli on 2010-12-12
wow! lots of different opinions!
anyway I switched back to having it in the default position as all the buttons in it got messed around.

but now, funny thing: my trash and show desktop icons are on the lower left corner (prior they were on the right) and their order changes randomly at each system startup (i.e., sometimes trash is the extreme left and next to it there is show desktop, other times it shows up the other way around!)

crazy!

---

### Post by Krytarik on 2010-12-12
> **glósóli said:**
> wow! lots of different opinions!
anyway I switched back to having it in the default position as all the buttons in it got messed around.

but now, funny thing: my trash and show desktop icons are on the lower left corner (prior they were on the right) and their order changes randomly at each system startup (i.e., sometimes trash is the extreme left and next to it there is show desktop, other times it shows up the other way around!)

crazy!
Right-click on each item, then on "Move", after you have moved them to the right position;), right-click again on them and click on "Lock To Panel".

Greetings.

---

### Post by glósóli on 2010-12-12
> **Krytarik said:**
> Right-click on each item, then on "Move", after you have moved them to the right position;), right-click again on them and click on "Lock To Panel".

Greetings.

sorted (hopefully, will check at next reboots), awesome!
i'm such a n00b! :p

thank you!

---

