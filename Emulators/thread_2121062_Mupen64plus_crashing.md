---
title: "Mupen64plus crashing"
date: 2013-02-28
forum: Emulators
---

### Post by emanmcdow on 2013-02-28
I am new to Ubuntu, but not at all to emulators. The only n64 emulator I can find is Mupen64. So I open it, load a rom(majoras mask) and it instantly closes after I press start. I cannot find any solution similar to mine. A lot of people say stuff about plugins, what are these for and how should i use them? thanks!

---

### Post by deadflowr on 2013-03-04
Now are you runnning mupen64 or mupen64plus?
Mupen64 is outdated and development moved to mupen64plus.
Before Ubuntu 12.04, the repos included mupen64plus version 1.5-something-something.
12.04 and after includes mupen64plus version 1.9-something-something.
Version 1.5 included the gui which made launching game simple and all plugins worked out of the box.
Version 1.9 dropped the gui and runs via the command line.
There are however frontends available
[https://code.google.com/p/mupen64plus/wiki/ThirdPartyPlugins](https://code.google.com/p/mupen64plus/wiki/ThirdPartyPlugins)

If you've installed mupen64plus from the repos, look at the manpages on how to it setup
```
man mupen64plus
```

Unfortunately, I have found the gui frontends to be poor and have relegated myself to using the cli, which runs the games much smoother.
Look here for good references on how to change setting, especially the keyboard layout:
[https://code.google.com/p/mupen64plus/](https://code.google.com/p/mupen64plus/)

---

