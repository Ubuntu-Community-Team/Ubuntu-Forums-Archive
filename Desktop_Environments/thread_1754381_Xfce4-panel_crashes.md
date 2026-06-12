---
title: "Xfce4-panel crashes"
date: 2011-05-10
forum: Desktop Environments
---

### Post by VirusCollector on 2011-05-10
Hello,

In order to avoid the 11.04 total system upgrade, I compiled the only feature I wanted out of it-- XFCE 4.8 -- manually, and installed it myself. Had to symlink a few shared libs for some reason, but otherwise it works fine except that I can't log in normally.

In .xsession-errors, I get this message:
xfce4-panel: symbol lookup error: xfce4-panel: undefined symbol: xfce_panel_get_channel_name

However, I can only find this error by booting recovery kernel and su-ing to my user, then typing startx. Using the normal login page crashes and goes back to the same page, producing no errors at all in .xsession-errors. If I boot recovery, everything works but xfce4-panel.

Please help me out, panel is rather essential to the workings of XFCE.

---

### Post by ManualSparrow on 2011-05-10
My self-install of XFCE 4.8 didn't work perfectly either, although I was able to login and such. Ended up doing a fresh install of Xubuntu 11.04, which is snappier anyways.

---

### Post by VirusCollector on 2011-05-10
Blah, I don't want to though. Every new version has had things I really just don't want at all, and so when something significant comes out and I can install it myself without having to reinstall the whole OS AGAIN and redo every little personal change and script I have written...

And yeah, that's supposed to be the point of have separate /home and / partitions. Problem was, when I upgraded to 10.10, it didn't care about any of the settings I had in there and was so messed up I had to reinstall anyway!

---

### Post by ManualSparrow on 2011-05-10
Honestly, that's why I went with 11.04 - but I did make a copy of the home folder and any config files I wanted, so the transtitions was very simple.

---

### Post by VirusCollector on 2011-05-11
Problem solved: added PPA for 10.10 at Web Upd8. Only issue now is that my touchpad totally dies when I click on any settings pane's options, but whatever.

---

