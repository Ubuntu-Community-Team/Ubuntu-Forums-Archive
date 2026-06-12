---
title: "Starting Xmodmap on login (12.10)"
date: 2013-02-15
forum: Desktop Environments
---

### Post by buntzu on 2013-02-15
Hi there,

I'm a little confused about the automatic startup of Xmodmap. The web said that I just have to create

[LIST]
[*]an .Xmodmap file in my home folder or
[*]an .xinitrc or .xsession script in home or
[*]a startup application/command launching xmodmap
[/LIST]
but none of these worked oob.


After some messing around I found that adding a ***sleep*** instruction to my xmodmap script started via startup applications achieved the desired effect.


As I didn't find any kind of hints to sleep being necessary: is this really needed/intended? Should any of the other ways (plain .Xmodmap file or .xinitrc/.xsession script) work in QQ?


Thanks a lot for clarification.

---

