---
title: "aiglx/compiz on an intel i915 video card"
date: 2006-09-12
forum: Desktop Environments
---

### Post by catalasan on 2006-09-12
hi all,

just installed aiglx/compiz on my toshiba satellite m45-s331 running on dapper by following this excellent instruction:
  
[http://wiki.compiz.net/index.php/Aiglx/compiz_on_an_Intel_i915_video_card](http://wiki.compiz.net/index.php/Aiglx/compiz_on_an_Intel_i915_video_card)

everything seems to be working fine except when i select "system->quit" from the mainmenu that the system freezes.  i have to do "ctrl+alt+backspace" to restart it.

did any of you guys encounter this problem?

i very much appreciate any help,

val

---

### Post by ghotra on 2006-09-12
lol!  I have the same problem and so does someone else.  The count is at three now...which means it is _everywhere_ probably.

[http://www.ubuntuforums.org/showthread.php?t=254891](http://www.ubuntuforums.org/showthread.php?t=254891)

Sadly, no one repsonded to my post with a fix. Hopefully, we'll have better luck with this post.

Truly this is a BIG problem.  I need to be able to logout and shut my computer off, and I'd rather not resort to Ctrl-Alt-Backspace every time.

---

### Post by ronmarley1 on 2006-09-12
I'm not sure if this will help, but I had a similar experience, and was able to fix it.  When they changed the compiz settings applet from the compiz tray icon to the CSM, I figured that I could delete the gnome-compiz-manager, since it was no longer used.  Uninstall went fine and everything ran fine until I rebooted.  Then, just like you, my laptop would lockup tight when clicking System -->Quit.  I reinstalled gnome-compiz-manager and everything went back to normal.  Hope this provides insight...

---

