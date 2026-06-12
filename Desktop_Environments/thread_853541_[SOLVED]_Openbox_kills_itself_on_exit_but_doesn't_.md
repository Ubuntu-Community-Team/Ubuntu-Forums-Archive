---
title: "[SOLVED] Openbox kills itself on exit but doesn't logout. (All of a sudden)"
date: 2008-07-08
forum: Desktop Environments
---

### Post by PrimoTurbo on 2008-07-08
I have no clue why this started happening, I've been using openbox from the repos for the past couple of months with no problem. Today openbox started behaving oddly during exit, instead of logging out to GDM openbox began to just kill itself. I now need to press CTRL-ALT-BACKSPACE to get to GDM on exit.

The command openbox issues is "openbox --exit". 

How can this happen all of a sudden, the only change is that I installed KeyTouch to map my media keyboard but I don't see how this could affect openbox. I have tried restarting and this behavior continue. Any help to resolve this issue would be of great help thanks.

**EDIT:**
I just checked under GNOME and the same behavior happens! When I try to logout it looks like it just kills gnome-panel and I see a blank screen with my wallpaper. I also have to CTRL+ALT+BACKSPACE...

What is going on here? Thanks.

---

### Post by sayakb on 2008-07-08
Try:
```
killall openbox
```

---

### Post by urukrama on 2008-07-08
This seems to be [a known problem]("http://www.google.com/search?hl=en&client=opera&rls=en&hs=Bog&q=KeyTouch+problems+logout&btnG=Search"). 

Somewhere in [this bug report]("https://bugs.launchpad.net/debian/+source/keytouch/+bug/186713") a few possible solutions or workarounds are suggested.

---

### Post by PrimoTurbo on 2008-07-08
Thanks I will look into it.

---

