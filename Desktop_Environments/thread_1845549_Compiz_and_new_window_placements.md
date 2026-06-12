---
title: "Compiz and new window placements"
date: 2011-09-17
forum: Desktop Environments
---

### Post by cipherboy_loc on 2011-09-17
Interesting problem here. If I start up an application which starts maximized (Firefox, gEdit, etc) it's position is off by one or two pixels. When I move over to the workspace right of the current one, you can see a bit of overlap from the window. I then have to manually switch to which ever application is running on that workspace, because the other window still has focus. To get it to stay on only this workspace I have to click on the window decorations (as if going to move it), and then it aligns to only the current workspace.

NOTICE: I am not using Unity; this is in the GNOME "Classic" environment.

Stats:
Compiz 0.9.4.0
Ubuntu 11.04
gnome-session 2.32.1


Thanks,
Cipherboy

---

### Post by cipherboy_loc on 2011-09-17
Sorry about double post, but here are some screen shots:

[http://imgur.com/73HLi](http://imgur.com/73HLi)
[http://imgur.com/zFHgu](http://imgur.com/zFHgu)

---

### Post by raja.genupula on 2011-09-17
hey go with this 

[http://ubuntuforums.org/showthread.php?t=930911](http://ubuntuforums.org/showthread.php?t=930911)


all the best man

---

### Post by Copper Bezel on 2011-09-17
I have a similar problem while using the Emerald decorator, but it has to do with the decoration cropping - in your case, the window is actually moved to the right, huh? And I assume that un-maximizing the window and maximizing the window again fixes it?

raja, if there's a fix for this problem in the thread you linked, I'm not seeing it. Could you be a bit more specific?

---

### Post by cipherboy_loc on 2011-09-17
Raja:
I didn't read the whole thread but it didn't appear to relate to my issue. My issue is not that windows won't unmaximize, but instead that maximized windows are offset; shifting them to the right a pixel or two.

Copper Bezel:
I am not using the Emerald decorator. Indeed they do move to the right and it appears the decorations move with it. And yes, minimizing and then maximizing the window again appears to fix the issue for that one window. 


Cipherboy

---

### Post by Copper Bezel on 2011-09-17
I'd heard of problems in Compiz with windows scooting their way off to the right when opened and closed, but that was fixed before I upgraded to 11.04 and seems unrelated to your issue.

It's certainly a Compiz issue. What window placement method do you have set in CompizConfig for the "Place Windows" plugin? Does changing it have any effect?

---

### Post by cipherboy_loc on 2011-09-18
Copper Bezel:
Modifying the Place Windows plugin does not have any effect for me. I tried disabling it last night but it didn't help. 

A list of enabled plugins is as follows:
```

Composite
GNOME Compatibility
OpenGL
Desktop Cube
Expo
Rotate Cube
Show desktop
Viewport Switcher
Window Decoration
Wobbly Windows <- I have tried modifying the values but it doesn't effect placement.
JPEG
PNG
SVG
Text
Compiz Library Toolbox
Crash handler
Detection
Mouse position polling 
Regex Matching
Resize Info
Wallpaper
Workarounds
Grid
Move Window
Resize Window
Ring Switcher
Scale

```



Thanks,
Cipherboy

---

### Post by Copper Bezel on 2011-09-18
I don't honestly know, then, and I hope someone else has experienced your exact problem and can help. I did try something very redundant, which was to set a window rule in the Window Rules plugin to set windows with "state=maxhorz" as maximized, but it didn't have any effect on my problem, and it's not very likely to help yours, either (but it might be worth the shot.)

---

### Post by MeduZa on 2012-01-21
I have the same problem with dual screen, I did a lot of test, but nothing fix the problem, emerald made the problem bigger, but gtk-windows-decorator also have the problem, the window content fix his position if you click the decoration.

---

