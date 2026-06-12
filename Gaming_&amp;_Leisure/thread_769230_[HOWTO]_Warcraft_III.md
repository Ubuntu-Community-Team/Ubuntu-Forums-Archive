---
title: "[HOWTO] Warcraft III"
date: 2008-04-26
forum: Gaming &amp; Leisure
---

### Post by spamoom on 2008-04-26
This works with every version of ubuntu that I've installed (including hardy).

1. Install wine-doors using a .deb - [direct link]("http://www.wine-doors.org/releases/wine-doors_0.1.2_all.deb") - [download page]("http://www.wine-doors.org/wordpress/?page_id=3") -
2. Run WineDoors from Applications >>System Tools >> Wine-Doors and let it configure wine
3. Once the main wine-doors window comes up search down the list for DCOM 98 and press install followed by Apply
4. Close winedoors once that has completed and insert your warcraft III ROC cd. Browse to your cd and double click on install.exe, follow the installation as you would on windows.
5. Then do the same for the frozen throne if you want.
6. To run it manually, you can put this command in console, the first for ROC and the second for TFT. Opengl is added to stop it using directx which dramatically increased performance.
```
wine "/home/[COLOR="Red"]username[/COLOR]/.wine/drive_c/Program Files/Warcraft III/Warcraft III.exe" -opengl
wine "/home/[COLOR="Red"]username[/COLOR]/.wine/drive_c/Program Files/Warcraft III/Frozen Throne.exe" -opengl
```
7. The installers automatically make the correct launchers for you on the desktop that run through wine. You can delete the .lnk files however as they are not used.

This is my first proper post, so give me feedback if it is/isn't right. :)

---

