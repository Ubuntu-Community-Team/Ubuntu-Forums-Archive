---
title: "AWN dock Places menu not working as it should"
date: 2011-02-19
forum: Desktop Environments
---

### Post by BigSilly on 2011-02-19
Dunno if anyone here can help, but I've recently decided to set the top Gnome panel to Autohide and have set the various things I would use it for onto my AWN dock. Anyway, to cut a long story short, it's all working brilliantly but for one thing. When I click the Places applet and select my spare FAT32 storage partition (which lists correctly as 67Gb Media), nothing happens. It doesn't mount it or present it as a browsable folder as the Gnome menu usually and properly does. If I go to the Home menu first and then select it from the left in Nautilus, it works as it should, but trying to go directly from the AWN Places applet results in nothing.

Any ideas?

---

### Post by kerry_s on 2011-02-19
have you right clcked-> applet preferences & set the file manager
file system-> usr-> bin-> nautilus

---

### Post by BigSilly on 2011-02-19
Thanks for your reply. Sorry but I can't seem to see that in the right click context menu. If I right click the Places menu on the dock, it brings up the Dock Preferences, and there's nowhere to set the setting you mention from within that menu. Well, not that I can see anyway. Let me know what you think.

---

### Post by kerry_s on 2011-02-19
i don't use that applet, but when i add it, it's there in mine, are you using the latest version from ppa?
the 1 in the repo is old.
[https://launchpad.net/~awn-testing/+archive/ppa](https://launchpad.net/~awn-testing/+archive/ppa)

---

### Post by Copper Bezel on 2011-02-19
Which Places menu are you using? There are several.

The most dependable one IMO is the one that comes with the Cairo Main Menu.

---

### Post by stinkeye on 2011-02-19
Could also try using the YAMA applet (yet another menu applet) contained in the
**awn-applets-python-extras** package.
Behaves the same as the gnome-panel Main Menu applet.

---

### Post by BigSilly on 2011-02-20
> **Copper Bezel said:**
> Which Places menu are you using? There are several.

The most dependable one IMO is the one that comes with the Cairo Main Menu.

That's the one I'm using. :confused: :D  It just says "Dock Preferences", "Remove icon", and "About Cairo Menu" when I right click it.

> **kerry_s said:**
> i don't use that applet, but when i add it, it's there in mine, are you using the latest version from ppa?
the 1 in the repo is old.
[https://launchpad.net/~awn-testing/+archive/ppa](https://launchpad.net/~awn-testing/+archive/ppa)

No I'm using the one in Maverick's repo. Didn't realise it had progressed any since version 0.4.0. Ah well panic not. I'll have to add the new repo or hang on for Natty. Thanks for your replies all. :)

---

### Post by rvchari on 2011-02-20
> **stinkeye said:**
> Could also try using the YAMA applet (yet another menu applet) contained in the
**awn-applets-python-extras** package.
Behaves the same as the gnome-panel Main Menu applet.

better try to use awn-trunk instead of awn. you can find that in ubuntu software center. before installing awn-trunk / awn-trunk-applets / etxtras... uninstall prev verion of awn. you have better options and preferences in awn-trunk.

i think i had googled it and got it installed after understanding from the google info.

follow this link => [http://www.webupd8.org/2010/06/awn-lucido-gets-its-own-ppa.html](http://www.webupd8.org/2010/06/awn-lucido-gets-its-own-ppa.html)

---

