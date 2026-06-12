---
title: "ATI + XGL + Beryl : window decorations for 3D apps on"
date: 2007-07-31
forum: Desktop Effects &amp; Customization
---

### Post by DavidTingdahl on 2007-07-31
I'm running Kubuntu Feisty with beryl + XGL with ATI mobility radeon 9700 (fglrx). Works really slick

XGL is running on display :1.0 and I manged to start a 3D application (google earth) by launching it on the display :0.0 instead, using

googleearth --display :0.0

I never disabled the composite extensions in the xorg.conf file as all the howto's told me to. This would probably not have worked if so, I guess.
googleearth performs well but when running on this display, it appears on top of all XGL windows (and on top of the desktop cube as well). The google earth window has no window decorations so it's impossible to resize or minimize. Thus I have to close it if I want to use the reest of the desktop.

Now I wonder if this can be solved by:

A: any way of getting the KDE window decorations to work for the programs I run on the display :0.0 while running Beryl at the same time on display :1.0

B: If there is a terminal command that can minimize/maximize the open googleearth window or some command that makes all windows of display :0.0 invisible or similar.

Thank's you for response

/David

---

