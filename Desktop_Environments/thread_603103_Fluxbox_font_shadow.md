---
title: "Fluxbox font shadow"
date: 2007-11-04
forum: Desktop Environments
---

### Post by Steve Fisher on 2007-11-04
I'm able to create a nice red "shadow" effect behind the title of my Menu by doing this:
```
menu.title.font.effect: shadow
menu.title.font.shadow.color: #7e201c
menu.title.font.shadow.x: 1
menu.title.font.shadow.y: 1
```
... but I cant seem to get the syntax right to do the same thing on an active window title. I've tried it like this:
```
window.label.focus.font.effect: shadow
window.label.focus.font.shadow.color: #7e201c
window.label.focus.font.shadow.x: 1
window.label.focus.font.shadow.y: 1
```
... which to me seems the logical way of doing it, but it doesn't work. What's the correct syntax, or can it even be done?

---

