---
title: "emacs vs gnome-shell"
date: 2012-02-27
forum: Desktop Environments
---

### Post by o1e9 on 2012-02-27
Hi,

I am having strange window re-map problems with emacs 23.1 using gnome-shell on Oneiric.  susped-frame (Ctrl-Z) does work as minimize/restore using gnome-shell however after restore the frame is not respnding: scrollbars and editor part of the frame/window is frozen with picture it had prior C-Z.  Nonetheless F10 menu is available no problem and it is possible to open a new frame C-X 5 2 and close the frozen one.  If I activate minimize/restore using window manager options then Emacs behave all right.

I suspect Emacs frame is sleeping because still thinks it is in minimized state.  The reason is why Emacs does not receive re-map from mutter?

I never ever had issues with C-Z using Emacs and it definitely works using classical desktop or Unity.

Any tips would be welcome indeed.

---

### Post by cortman on 2012-02-27
Have you tried

```
M-x redraw-display
```

in emacs?

---

### Post by o1e9 on 2012-02-27
> **cortman said:**
> Have you tried

```
M-x redraw-display
```

in emacs?

Nope, did not help however I have found a workaround: resize window and it is possible to regain the control.  It may be annoying changing size or maximize/restore every time frame is un-minimized, if anyone has been workaround, please, let me know :)

---

