---
title: "GNOME Panel + Window List + Tooltips"
date: 2007-07-23
forum: Desktop Effects &amp; Customization
---

### Post by ryanVickers on 2007-07-23
I would like to know if there is some way to turn off the tooltip that pops up with the name of a window in it when you haver over the window's bar in the list area?  I have beryl so I have the previews with names turned on so I don't need the built in tooltips, and anyways, can't you just read them!?  It really is just an imperfection in my system and the less of those the better! :)  So is there a way to turn them off?  I know with emerald you can turn off the window buttons' (close, minimize, etc.) tooltips...

---

### Post by Voynix on 2007-07-23
I think this may work. Open gconf-editor, navigate to apps /panel/global and untick tooltips_enabled. However this will remove all tooltips for all applications.

Cheers

---

### Post by ryanVickers on 2007-07-23
No, that's just for launchers and of the sort.  I'm surprised the feature is hidden away like this (assuming it even exists)!

---

### Post by Arthur Archnix on 2007-09-27
It seems to be a bug. Likely won't get fixed. Oddly enough, works fine in Debian Lenny.

[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=3068965](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=3068965)

---

### Post by ryanVickers on 2007-09-27
> Open gconf-editor, navigate to apps /panel/global and untick tooltips_enabled. However this will remove all tooltips for all applications.
I think that because it's in the "panel" section, it probably won't effect anything but the panels :KS

but then, in theory, it should effect *everything* in the panels then at least...:confused:

---

### Post by Arthur Archnix on 2007-09-27
Like I said, it's a bug. The correct action is to disable tooltips in gconf-editor, but this doesn't work in Feisty. People with compiz-beryl can set tool-tips transparency to 100% as a workaround.

---

