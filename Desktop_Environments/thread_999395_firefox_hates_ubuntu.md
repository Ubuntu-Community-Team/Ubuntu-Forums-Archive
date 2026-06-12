---
title: "firefox hates ubuntu"
date: 2008-12-01
forum: Desktop Environments
---

### Post by zero777zero on 2008-12-01
it's official, firefox hates ubuntu. sometimes (often but not always) when i start firefox it defaults to a fullscreen (see below, no its not cropped). it goes fullscreen and the ubuntu toolbar disappears.

[IMG]http://lh6.ggpht.com/_ItkAF585hc8/STSUsBy53UI/AAAAAAAABSo/ctJgB72QZl0/s800/Screenshot.png[/IMG]

then when i push F11 it enter "proper" fullscreen mode (no toolbar, but it has an X button in the top right hand corner).

i'm now on 8.10, but i had the problem on 8.04 (only then i didnt know about F11 and was fizuk'd). latest version of firefox.

wtf

---

### Post by evildragon2 on 2008-12-02
Temporary fix: Run in terminal this command:

```
metacity --replace
```

Permanent: The glitch can be caused by Compiz (happened to me) turn it off in System -> Preferences -> Appearance -> Visual Effects and choose none.

Another reason might be a faulty Firefox installation and reinstalling will fix it.

---

### Post by madverb on 2008-12-02
[http://ubuntuforums.org/showthread.php?t=992666](http://ubuntuforums.org/showthread.php?t=992666)

More info there.

---

### Post by zero777zero on 2008-12-02
thanks for the replies. i don't believe its a faulty install since i've had this problem on prev installs of ubuntu.

in case any devs are looking at this thread, this seems like one of those emminent-fix-need bugs.

i cant imagine some noob being stuck in ff too happy.

---

