---
title: "Compiz Fusion Problem."
date: 2007-09-20
forum: Desktop Effects &amp; Customization
---

### Post by phizikal on 2007-09-20
I used the CF bash script install Compiz and all of it's components. I couldn't find Compiz Manager in the menus or anything. I tried running Compiz through shell and this was my output.

# compiz
compiz (core) - Warn: SmcOpenConnection failed: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
compiz (core) - Error: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
compiz (core) - Fatal: No manageable screens found on display :0.0

"

Yes, I do have my nvidia drivers up to date.

---

### Post by chuckyp on 2007-09-20
Try hitting alt+F2 and typing in compiz --replace not just compiz.  Then if you want to go back to regular. Hit alt+F2 and type in metacity --replace.  If you want the settings manager under preferences you need to sudo apt-get install compizconfig-settings-manager

---

### Post by phizikal on 2007-09-20
I found the settings, i didn't restart my x server.

When I replace my window decorations to compiz or emerald, I lose my borders.

I also found an error on running a game on wine, it says I need libGL or openGL....something like that.

---

### Post by phizikal on 2007-09-20
erm?.......... No help?

---

