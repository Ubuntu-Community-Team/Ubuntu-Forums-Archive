---
title: "CCSM Installed, but certain plugins aren't working like they should."
date: 2007-12-29
forum: Desktop Effects &amp; Customization
---

### Post by wisemanleo on 2007-12-29
I'm an ubuntu-addict, but still somewhat of a newb. 

I've recently formatted by computer (compiz was working perfectly before then), and just finished reinstalling Compiz. The engine seem to be working, but there's certain plugins that aren't working like they should. I'll list the problems that I've discovered so far:

[LIST]
[*]CCSM > Desktop Size > Horizontal Virtual Size won't change from 2 to 4. Right now it's set at 4, but I still only have 2 desktops. Consequently, the cube won't work.
[*]The Ring-Switcher plugin is set on, but Super-Tab won't activate it, even though that binding is set. The regular Alt-Tab still works for switching windows the old-school way.
[/LIST]

There might be other things about the CompizConfig Settings Manager that aren't working and haven't discovered yet. I suspect there's probably a root-cause, maybe I forgot to add in an extra repository or missed some plugin installations.

Any help or pointers to pre-existing guides would be greatly appreciated!

---

### Post by anagor on 2007-12-29
what is the number of virtual desktops you have there? I think that they may interfere one with another.
regarding the ring switcher, there is another switcher as you know, the shift switcher which also defaults its key binding to super-tab, maybe it is enabled also, in that case you probably want to disable it.
also check for global shortcuts in the system itself, not related to ccsm, if this combination is defined somewhere in the system it will take precedence over compiz.

---

### Post by Phurious on 2007-12-29
To enable the cube your settings under Compiz setting should look like this
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=54634&d=1198989802[/IMG]

---

