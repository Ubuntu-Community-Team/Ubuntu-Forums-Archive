---
title: "[SOLVED] unable to access virtual terminals"
date: 2007-07-31
forum: Desktop Environments
---

### Post by quantumcheese on 2007-07-31
ctrl + alt + f[1-6] used to take me to six virtual terminals.  Now, however, these key combinations they do nothing.

Following a similar posting from years ago, I shut down gdm, and then I had access to them.  I restarted gdm and could still switch among the 6 ttys and x-server until I logged in (via x).

---

### Post by quantumcheese on 2007-07-31
After some playing around, I realized that I can in fact only not switch virtual terminals while logged into Fluxbox window manager.  I'd still appreciate if anyone has ideas, but I think I'll go bug the fluxbox people about this.

---

### Post by quantumcheese on 2007-08-14
The real issue was a bad workaround I was trying with my right alt key, which I had remapped to Alt_R (from ISO_Shift_Level3); so when I tracked down the .xmodmaprc as the problem, I searched this forum and found that it was an xorg.conf error, commented out a line, and now can both access virtual terminals and use my right alt button as alt (mod1).

---

