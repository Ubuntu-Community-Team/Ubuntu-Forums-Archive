---
title: "Xephyr/Xnest issues: Bad setup/Can't use OpenGL"
date: 2008-09-26
forum: Desktop Environments
---

### Post by DOS4dinner on 2008-09-26
Ubuntu 8.04
 Pentium 4 2.6ghz 
ATI Radeon 9800 128mb graphics card (tested and proved to be set up right).

I've been trying to get an old 256 color windows app to run in wine, but I need Xephyr/Xnest to do it (following a tutorial [here]("http://wiki.winehq.org/256ColorsWorkarounds")). However, neither of them (or VNC) can use OpenGL for reasons I don't know.

I get this when I run Xyphyr with the command Xephyr :1 -ac -screen 800x600x8; DISPLAY=:1 wine name_of_application:

```
[1] 16578
name@name-desktop:~$ expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
expected keysym, got XF86KbdLightOnOff: line 70 of pc
expected keysym, got XF86KbdBrightnessDown: line 71 of pc
expected keysym, got XF86KbdBrightnessUp: line 72 of pc
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 1493 requests (1493 known processed) with 0 events remaining.
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.
Application tried to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.

[1]+  Exit 1                  Xephyr :1 -ac -screen 800x600x8

```

This came up from the wine debug info when using VNC and Wine:

```
Xlib:  extension "GLX" missing on display ":2.0".
err:wgl:X11DRV_WineGL_InitOpenglInfo  couldn't initialize OpenGL, expect problems
```
The Xephyr window does come up, but no program will load. It is just a blank screen. What am I doing wrong? Thanks in advance. I really just want to play sonic CD...:frown:

---

