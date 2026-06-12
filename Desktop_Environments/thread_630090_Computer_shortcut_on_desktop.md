---
title: "Computer shortcut on desktop??"
date: 2007-12-03
forum: Desktop Environments
---

### Post by Lvcoyote on 2007-12-03
Is it possible to put a "Computer" shortcut on the desktop??  I'm tired of having to go to Places/computer to get there....LOL

---

### Post by Thanoulis on 2007-12-03
Sure. Run gconf-editor and go to apps->nautilus->desktop. in the right panel enable the "computer icon visible" check box. That's all!

---

### Post by Lvcoyote on 2007-12-03
gconfig-editor does nothing when run in terminal and I have no nautilus option under apps....:confused:

---

### Post by Lvcoyote on 2007-12-03
Must have been typing wrong, it worked!!  Thanks for the information!

---

### Post by richyrichuk on 2008-01-25
sweet...thanks

---

### Post by rosegarden78 on 2008-01-25
So that's how you change your desktop icons.  Does this work for XFCE desktop?  Are there separate commands for KDE as well?

---

### Post by opscure on 2008-01-25
You can usually change any desktop or window manager related options through the config files in your home directory.  For example, xfce4 desktop configuration files are located in ~/.config/xfce4/desktop/
It's probably a good idea to get familiar with these config files if you want to do custom changes since the gui tools will only let you do so much.

---

