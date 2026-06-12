---
title: "[mac] Wine and X11 on Mac OS X (involves OpenGL, Steam)"
date: 2009-03-16
forum: General Help
---

### Post by Nicholas Escalona on 2009-03-16
Not an Ubuntu question.

So, I'm trying to get Wine working properly on Mac OS X 10.5.6. I'm using the MacPorts latest version of wine, 1.0.1_2, and the MacPorts latest version of xorg, 20090218. I can run Notepad just fine on this setup.

I'm trying to get Steam working. Installation of Steam went fine, and I can load the program. When I move the cursor over any tab of Steam that includes content displayed by Gecko, loads of messages appear in the wine console (one message for every pixel the cursor moves when over that window). Here is a log of the output.

[http://rafb.net/p/eQo60X90.html](http://rafb.net/p/eQo60X90.html)

lines 1-3 appear every time I run anything with Wine
lines 4-19 are initializing Steam, no visual output yet
lines 20-(~31) are initializing Steam, "connecting steam account" dialog displayed
lines (~32)-140 are initializing Steam, main window loading
lines 140-202 are moving the cursor on Gecko pages
lines 203-546 are immediately after clicking to install a game through Steam     <---- important part
Then Steam crashes. X11 remains open.

My problem appears to be a lack of OpenGL support in my version of xorg. I'm not sure where to start with this. Help appreciated!

---

