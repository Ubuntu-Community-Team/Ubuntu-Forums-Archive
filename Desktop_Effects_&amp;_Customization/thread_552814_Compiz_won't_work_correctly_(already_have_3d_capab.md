---
title: "Compiz won't work correctly (already have 3d capabilities)"
date: 2007-09-17
forum: Desktop Effects &amp; Customization
---

### Post by alan_daniel on 2007-09-17
I'm running Feisty on an IBM T43 with an ATI card. I have already set up fglrx, and opengl seems to be working fine (I can run the 3d gears perfectly). I have installed compiz and want to get it working, and have set up XGL to run a Gnome session. I can get into that Gnome session just fine without any errors, and everything works fine. My problem comes when I try to start compiz in that XGL session. Here's the output when I run compiz --replace

```
compiz (core) - Fatal: GLX_EXT_texture_from_pixmap is missing
compiz (core) - Error: Failed to manage screen: 0
compiz (core) - Fatal: No manageable screens found on display :0.0

```

I lose all window borders and cannot switch between windows, which makes me think that I have ultimately lost control of my window manager. I have tried searching around on the internet for an answer to this, but I have just gone in a circle trying to find an answer. Any help is appreciated.

Oh, and I've already tried the gnome-compiz-manager, and that does the same thing. I have the emerald manager installed, but when I start that and select a theme (after running emerald --replace), nothing happens.

---

### Post by phizikal on 2007-09-17
i am having the same problem, i do have 3d capabilities also.

i am using an nvdia tho.

edit..

now im getting 

"# compiz
compiz (core) - Warn: SmcOpenConnection failed: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
compiz (core) - Error: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
compiz (core) - Fatal: No manageable screens found on display :0.0
"

---

