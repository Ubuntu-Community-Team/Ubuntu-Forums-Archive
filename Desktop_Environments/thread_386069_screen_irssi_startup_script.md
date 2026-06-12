---
title: "screen irssi startup script"
date: 2007-03-16
forum: Desktop Environments
---

### Post by mig27 on 2007-03-16
I've quickly realised the potential of irssi and screen when used together, and have it set up nicely, but would like to know how to write a script to have an irssi session (named irc) started up in screen detached at boot, ready for re-attachment whenever I need it.

I've found a few examples of this online, but nothing that has worked properly and I'm not sure why.

Any scripts that anyone is using or links would be much appreciated.

---

### Post by mig27 on 2007-03-19
Bump, any help would be gratefully recieved.

---

### Post by yannick_LM on 2008-02-11
I believe you just have to put something like:

```
screen -t irc irssi
```

at the end of your ~/.screenrc file

---

