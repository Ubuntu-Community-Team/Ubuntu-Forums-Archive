---
title: "menu doesn't focus"
date: 2016-01-15
forum: Desktop Environments
---

### Post by monkeybrain20122 on 2016-01-15
In Ubuntu 15.10, when switching applications with compiz's scale plugin and hot corner I notice that the menu on the top panel doesn't change along with the applications' windows. e.g If Firefox is in front of terminal, use scale's hot corner to pick the terminal, the terminal's window comes into focus, but the top menu still shows' firefox's unless right click the panel or hit the hot corner again.  Here both Windows are maximized and I have set to use local menu. Also switching windows via other means such as alt+tab or Compiz's shift switcher is fine.

This may be related: if I switch to use global menu from settings then the menus for non maximized applications simply disappear unless placed right under the top panel.

I am wondering if this is a bug or something about my settings. Can anyone check? Thanks.

---

### Post by monkeybrain20122 on 2016-01-15
It is sort of like this [https://bugs.launchpad.net/unity/+bug/881707](https://bugs.launchpad.net/unity/+bug/881707) but the bug has expired. Any way to resurrect it?

---

### Post by monkeybrain20122 on 2016-01-15
Ok. Figured it out. It is my fault. I have been playing with unity-tweak tool and set Window Manager > Additional > Window focus mode to "sloppy", changed back to "click" now it works as before. Sorry for the false alarm.

---

