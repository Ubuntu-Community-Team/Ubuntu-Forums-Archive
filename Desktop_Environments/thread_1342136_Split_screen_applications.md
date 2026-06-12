---
title: "Split screen applications"
date: 2009-11-30
forum: Desktop Environments
---

### Post by gabello on 2009-11-30
Hello, is there any application for xfce that allows users to define more areas on the same desktop and each to behave like a separated desktop (e.g. maximize a window will make the window fill only that area not full screen). Thank you.

---

### Post by Simian Man on 2009-11-30
I don't know of anything that does exactly what you describe, but there is a way to get the same effect.

You can use Xfwm's fill window feature to make windows fill all space they can without overlapping other windows.  Open Preferences->Window Manager and look for "Fill Window" under the keyboard tab and assign it a keyboard shortcut (I use Ctrl-Alt-Space).

Then you can arrange windows on your screen how you want them, but with gaps between and use the Fill Window command to make them flush.  Hard to explain, but if you try it you'll see what I mean :).  This is actually one of my favorite things about xfwm.

---

### Post by gabello on 2009-11-30
Thanks, yes it does help, it would be better if I had a way to apply the "fill window" effect to all windows with one keystorke and not individual for each item.

---

### Post by exoren22 on 2009-11-30
> **gabello said:**
> Thanks, yes it does help, it would be better if I had a way to apply the "fill window" effect to all windows with one keystroke and not individual for each item.

Well, that would be ambiguous behaviour. When you try to apply this to all windows, which ones do you expand in which directions? Do you move the big one to the small one, the small to the big, meet them halfway? The extra 10 seconds of key-stroking cannot be all that bad, right?

---

