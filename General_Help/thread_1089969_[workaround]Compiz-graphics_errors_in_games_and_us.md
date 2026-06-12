---
title: "[workaround]Compiz-graphics errors in games and user switching issues"
date: 2009-03-07
forum: General Help
---

### Post by fdm on 2009-03-07
[Problem]
  when compiz is running i experience grapical errors such as flickering in many 3d games native and wine. playing videos with xv is not possible, and the alternatives are grim.fast user switching results in corrupted screen(pressing Ctrl+Alt+F6 then Ctrl+Alt+F7 will let you log back in; switching is impossible)

[Workaround]
  create two launchers and place them on one of your gnome toolbars one using the command to start compiz:
> compiz
and the other to kill it:
> killall compiz && killall compiz.real
you simply press the kill button when you need to run a game or switch users or run anything you normally can't. then press the start button to load everything back to normal with all running programs intact. while compiz is disabled, the bars above your programs will disappear; this is expected behavior and can work to your advantage.

[Setting up your games]
  you can either use the fullscreen option or you can set it up in window mode but at the resolution of your monitor. this concept works with the wine virtual desktop too, providing a flawless fullscreen game environment. on a side note, this fixed Warcraft III's cursor glitch that maked it difficult to scroll left and right ingame.

as far as i can tell, everything runs flawlessly so i thought i would share. hope this helps especially for the people like me who will loose driver support after ati catalyst 9.3.

---

