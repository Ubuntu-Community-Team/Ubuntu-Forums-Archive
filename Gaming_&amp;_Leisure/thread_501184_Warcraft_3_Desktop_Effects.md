---
title: "Warcraft 3 Desktop Effects"
date: 2007-07-14
forum: Gaming &amp; Leisure
---

### Post by leetcharmer on 2007-07-14
When I have desktop effects on in feisty, I can see the top and bottom bars of gnome-panel in my fullscreen game of warcraft 3.  I don't want to see those because it affects in-game scrolling.  Know how I can remove the gnome panels while playing the game?  Thanks

---

### Post by Toxicity999 on 2007-07-15
That's a problem with Wine Fullscreen and compositing. Set up the panels so you can hide them with the roll away buttons. Best, and easiest option. (right click the panel, Properties, Show Hide Buttons tick box.)

---

### Post by Outrunner on 2007-07-15
> **leetcharmer said:**
> When I have desktop effects on in feisty, I can see the top and bottom bars of gnome-panel in my fullscreen game of warcraft 3 -



Then may I suggest you disable Compiz(Desktop Effects) while playing Warcraft? ;)

---

### Post by leetcharmer on 2007-07-15
> **Outrunner said:**
> Then may I suggest you disable Compiz(Desktop Effects) while playing Warcraft? ;)

:P  What if I want to cube while playing?  (so I can answer an IM or something on a different workspace)

---

### Post by Outrunner on 2007-07-15
Not sure about that. I'm sure there's a workaround, though - either for switching workspaces(without Compiz) or scrolling, but i can't think of any at the moment :-k

---

### Post by leetcharmer on 2007-07-17
I'm getting an error when trying to install The Frozen Throne, wanna take a stab at it?
> 
leetcharmer@jBox:/media/cdrom1$ wine install.exe 
err:module:load_builtin_dll failed to load .so lib for builtin L"comctl32.dll": /usr/bin/../lib/wine/comctl32.dll.so: invalid ELF header
err:module:import_dll Loading library comctl32.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") failed (error c000007a).
err:module:import_dll Library SHELL32.dll (which is needed by L"E:\\install.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"E:\\install.exe" failed, status c0000135

---

### Post by xxrealmsxx on 2007-07-18
I had a similiar problem installing Warcraft III from a .bin/.cue file. It worked after I got the actual cd. Check your settings in winecfg to see if cdrom1 is selected as a drive.

---

