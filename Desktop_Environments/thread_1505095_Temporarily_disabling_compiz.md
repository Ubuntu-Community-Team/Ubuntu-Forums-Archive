---
title: "Temporarily disabling compiz?"
date: 2010-06-08
forum: Desktop Environments
---

### Post by X-Windows on 2010-06-08
I have a question that I'm sure many of you gamers have encountered, how to run a game without compiz. My question is, is it possible to either run a program without applying compiz effects (something like -nocompiz) or disable compiz while a program is running (-disablecompiz). It would make sense to have something like a master "on/off" switch for compiz, I just cant find a way to turn it off via the terminal. Even better would be some way to setup a keyboard shortcut to toggle it. If this is not possible, I think I'll make a suggestion to compiz.

---

### Post by pwicken on 2010-06-09
Press Alt+F2:
```
metacity --replace
```
and to return to compiz
```
compiz --replace
```

---

