---
title: "[SOLVED] Wine refresh rate after exit"
date: 2008-12-22
forum: General Help
---

### Post by potam on 2008-12-22
Hello guys,

I have an 1280x1024@75 monitor. When I run a fullscreen game with wine I figured out I have to use ForceRefreshRate registry key to force wine use 75Hz. That part works, but when I exit the game (wine closes), the refresh rate falls back to 60Hz instead of 75Hz (or the value before the game).

What is wrong?

System is Intrepid, video card is Nvidia Geforce FX5500, drivers installed, compiz.

---

### Post by potam on 2008-12-24
FYI, the complete, step-by-step solution is:
[LIST=1]
[*]Open regedit in wine (ALT+F2, regedit)
[*]Create Create HKLM\Software\Microsoft\DirectDraw key
[*]Create HKLM\Software\Microsoft\DirectDraw\ForceRefreshRate dword with a value 75 (75Hz, the maximum refresh rate of my TFT)
[*]Open /etc/X11/xorg.conf (remember:backup!!!) on Section Screen the display mode should be this: Modes "1280x1024_75" "1024x768_75" "800x600_75", note the underline and refresh rate at the end of each resolution
[*]If you have nvidia card, and you do not use 2 monitors add Option "DynamicTwinView" "False" to section screen.
[*]Save the file, restart X, and all set, during gaming in wine the refresh rate will be 75, and after exit too.
[/LIST]

---

