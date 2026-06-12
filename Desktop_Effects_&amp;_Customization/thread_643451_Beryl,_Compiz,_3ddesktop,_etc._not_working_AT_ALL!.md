---
title: "Beryl, Compiz, 3ddesktop, etc. not working AT ALL!!!!!"
date: 2007-12-17
forum: Desktop Effects &amp; Customization
---

### Post by StevenP9891 on 2007-12-17
Whenever I try to use any type of advanced 3d desktop environments such as Beryl, or Compiz my screen goes into a black command-line and I get a few error messages, following with a restart of the system back to the login screen.

The error messages are [COLOR="Red"]Mounting HGFS Shares.......Failed[/COLOR] (around the top)    and [COLOR="Red"]CPU Frequency Scaling Not Supported[/COLOR] (around the middle) and a [COLOR="Red"]nonexistent directory[/COLOR] right above it:

[IMG]http://i24.photobucket.com/albums/c40/ElmoBro23/beryl.jpg[/IMG]

---

### Post by dabl on 2007-12-18
I certainly could be wrong, but I don't think there's any relationship between the powernowd stuff and Compiz performance.  BTW, you'll never have Beryl and Compiz running on the same platform -- at least not at the same time.  Beryl is not being developed (for quite awhile now).

Your basic steps to get Compiz working are:

1. Install a video driver that supports 3D accleration (verify with glxgears or the like).
2. Install the compiz and emerald packages (verify with emerald --replace and observe the window decorations being replaced).
3. Enable compiz and use compiz configuration settings manager (ccsm) to set up the cube, rotation, skydomes, wobbly windows, etc. etc.

HTH.  :)

---

