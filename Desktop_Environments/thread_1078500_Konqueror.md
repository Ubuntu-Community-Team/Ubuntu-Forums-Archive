---
title: "Konqueror"
date: 2009-02-23
forum: Desktop Environments
---

### Post by harsh1kumar on 2009-02-23
I have installed KDE 4 in kubuntu. My problem is that whenever I open knoqeror, 8 windows open. They have 3 tabs having same webpage which I had opened yesterday. After the 8 windows open all of the windows freeze and I am not able to do anything except kill the process. What do I do??

---

### Post by yther on 2009-02-23
I have no idea why it's doing what it's doing, that's quite strange, but its behavior sounds similar to what Firefox and Internet Explorer can do if they get hijacked.

Here's a suggestion:  Either open a Konsole or push Alt+F2 and type this.

```
konqueror about:blank &
```

That should start it and display nothing.  Then you can check your configuration to see if something changed your home page for you.

---

### Post by harsh1kumar on 2009-02-23
Thanks man, that did it. You are great:p

---

