---
title: "How can I restore XFCE panel settings?"
date: 2007-10-13
forum: Desktop Environments
---

### Post by jon.reeve on 2007-10-13
I don't know how it happened...maybe it had something to do with compiz...but now my XFCE panel is all messed up. The Xubuntu menu is now an XFCE menu, all the launchers are gone, and worst of all everything is left-aligned. Whereas before I had my clock on the right side and my Applications menu on the left, now it's all left-aligned with a lot of white space on the right, and it won't let me move any of the applets to the right side of the panel. I've tried everything I can think of, reinstalling xfce4-panel, reinstalling all the xubuntu-desktop packages, editing every customization setting in the panel manager, even taking a look at ~/.config/xfce4/panel/panels.xml which hasn't been much help at all. 

Is there a way I can load the default Xubuntu panel?  I just want to be able to put my clock on the left side of the panel and put the applications menu on the left.

---

### Post by jon.reeve on 2007-10-13
Ok nevermind, I just figured it out. In case anyone else has this problem for whatever reason, it can probably be solved by simply deleting the directory called ~/.config/xfce4/panel which will then force xfce4-panel to draw up a fresh one.

---

### Post by wulfhound on 2008-07-17
Thanks so much, this was driving me nuts. I believe it is something to do with Compiz.

I would thank you but maybe because this is archived, it isn't letting me?

L

---

