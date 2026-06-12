---
title: "top panel not drawn correctly"
date: 2010-12-07
forum: Desktop Environments
---

### Post by tomdelonge on 2010-12-07
Sometimes (almost always) when I log in to Ubuntu, the top panel is not 'drawn' perfectly. The left has always been fine (menus, shortcuts). But the right has issues. Most often the icons for wireless or custom applications are half there or sometimes only a white vertical line is there instead. Sometimes the profile name is half visible twice (meaning the first part of my name is drawn next to itself.

One solution I've found is to right click the panel, choose 'properties' and check 'show hide buttons'. I can then immediately uncheck it and everything is drawn correctly.

As you can imagine, it's getting annoying to have to do this so often.

What could be the issue?

---

### Post by lukeiamyourfather on 2010-12-07
What version are you running? If running an older version there might already be a fix for the issue in newer releases of Ubuntu.

---

### Post by tomdelonge on 2010-12-07
10.10

---

### Post by mcduck on 2010-12-07
As far as I can say this is related to the Indicator Applets, and there's no actual fix for it yet. Anyway, simply restarting the panel will usually get things working correctly; just hit Alt-F2 and run "killall gnome-panel".

Pretty much anything that forces the panel to re-draw itself will work.

---

