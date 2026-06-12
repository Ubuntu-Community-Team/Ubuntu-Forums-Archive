---
title: "firefox takes up entire screen"
date: 2008-12-21
forum: General Help
---

### Post by oilspot on 2008-12-21
I saw a post about this a while back... but I can't seem to find it.
 When I use firefox it takes up the entire screen. No close, minimize, etc buttons. And I can't see the bottom panel. 
 The frustrating part is that it will be fine for a while. Somehow or another I mess around and get it fixed (usually by going fullscreen, and then back). It will stay normal for a while, and then switch back.

---

### Post by howefield on 2008-12-21
F11 doesn't work ?

Sounds too easy to be the answer :)

---

### Post by oilspot on 2008-12-21
I searched for a while... then found this thread a few down from mine.

[http://ubuntuforums.org/showthread.php?t=793615](http://ubuntuforums.org/showthread.php?t=793615)

I think I'm getting some answers there.
 Hitting f11 twice takes care of it. I'm working with the other stuff right now so I don't have to use all kinds of tricks to make it run like I like.

---

### Post by jflaker on 2008-12-21
Already reported as a bug [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/99740](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/99740)

fix it/**Workaround :
Step 1 - Install compizconfig-settings-manager (sudo apt-get install
compizconfig-settings-manager)
Step 2 - Start ccsm (either from the commandline or by pushing Alt+F2 and
typing ccsm)
Step 3 - Click on "Workarounds" plugin in the "Utility"
section
Step 4 - Uncheck "Legacy Fullscreen Support".

---

### Post by rustic on 2008-12-29
Thanks.

I have been doing my own "work around" - shift-ctrl-H then fast switch to other windows from there to get my gnome panel back.

Phew.

Thought I was on the verge of a rebuild.

:KS:KS:KS:KS:KS

---

### Post by -kg- on 2008-12-29
> Step 2 - Start ccsm (either from the commandline or by pushing Alt+F2 and
typing ccsm)

Actually, when you install CCSM, the application can also be brought up by clicking "System/Preferences/Advanced Desktop Effects Settings."

A tad easier than pulling up a terminal window or the Run Application window.

---

