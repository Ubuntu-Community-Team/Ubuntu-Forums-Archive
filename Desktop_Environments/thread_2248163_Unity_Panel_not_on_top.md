---
title: "Unity Panel not on top"
date: 2014-10-12
forum: Desktop Environments
---

### Post by Brandon_MacEachern on 2014-10-12
This started happening out of nowhere, and is completely random, I am not sure what the trigger is.

[http://i.imgur.com/E4scGzt.png](http://i.imgur.com/E4scGzt.png)

Ideas?

The only fix seems to be to close every program open, then Unity goes back on top.

---

### Post by Brandon_MacEachern on 2014-10-12
EDIT:  Looks like it actually edited now.

---

### Post by grahammechanical on 2014-10-13
It is called the Dash and it should do exactly that. It should dash out and cover the desktop when we click the Ubuntu icon on the top of the Launcher or when we tap the super key. And then it should dash back in when we click an icon displayed in the Dash or on the Launcher. Why it is remaining on screen after an application (file manager in your example) has loaded, I do not know. Could it be because system resources are being used for some other tasks?

Regards.

---

### Post by mc4man on 2014-10-13
A search shows a few cases of the Dash opening under any open window(s) but no indication of cause or fix..
I guess you could try setting compiz/unity settings back to defaults, may help, may not.

If desired, 2 separate commands, in order - 
```
dconf reset -f /org/compiz/

setsid unity
```

---

