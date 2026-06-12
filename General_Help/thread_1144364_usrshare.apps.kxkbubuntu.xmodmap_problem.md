---
title: "/usr/share.apps.kxkb/ubuntu.xmodmap problem"
date: 2009-04-30
forum: General Help
---

### Post by sandyd on 2009-04-30
I have this major problem.
UNtil yesterday, kde was working fine. This morning, when i gooted up my computer and click on kde, a message came up that /usr/share.apps.kxkb/ubuntu.xmodmap was missing. Crated an empty file there, but got another error. IM sure there isn't supposed to be a file there, because my other linux box doesn't and it has kDE.

Some more info....

Desktop Environments that i have:


[LIST]
[*]Gnome
[*]XFCE
[*]Fluxbox
[*]KDE 3
[*]KDE 4
[*]KDE Nightly Neon
[/LIST]
Currently, only KDE 4 does not work. Kde neon (suprisingly) still works.

help me?

---

### Post by Helge on 2009-09-26
I got the same message in a log file on a new account that I had created on my laptop. The message was in ~/.xsession-errors.

The solution was to choose session in the login screen, where you enter username and password. I had forgotten to define if KDE or Gnome or something else should be used. Maybe it will help you too.

---

