---
title: "Screen-Keyboard not appearing when it should"
date: 2015-08-13
forum: Desktop Environments
---

### Post by xjas on 2015-08-13
Hey all,

Just installed Ubuntu-Gnome 15.04 on my convertible tablet/laptop (HP Touchsmart TM2). I essentially set this thing up to try Gnome 3.16, so I updated it from the PPAs (gnome3-staging.)
Everything seems to work fine except the Screen Keyboard (enabled from Universal Access) never appears when I want it. It comes up at the login screen and in the application search, but not when running other programs (e.g. browsers, terminal, gedit, LibreOffice, etc.) leaving me no way to enter text.

Is there a way to force it to appear every time I hit a text entry field, or at least pin a little icon to the top bar that will bring it up when I press it? It would be extremely useful to be able to use my machine as a tablet.

---

### Post by CantankRus on 2015-08-14
In Ubuntu/unity I run ...
```
onboard-settings
```
where I can set to auto-show when editing text.

---

### Post by xjas on 2015-08-14
I guess Onboard is a Unity app? I didn't have it by default, so thanks for pointing it out to me. I installed & configured it. Now it pops up every time the Gnome keyboard doesn't, which seems kind of kludgey but does the job.

It's a bit laggy though, any way to speed up the response time?

---

### Post by CantankRus on 2015-08-14
Don't use gnome-shell and didn't realize an onscreen keyboard was built in.
Not much help really.

---

