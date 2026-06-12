---
title: "Compiz Fusion and Ctrl+Alt+Mousewheel problem"
date: 2007-06-27
forum: Desktop Effects &amp; Customization
---

### Post by hyperair on 2007-06-27
Hi! Has anyone managed to get the Rotate cube to work with Ctrl+Alt+WheelUp/Down (Button4/Button5)?

I tried binding it in the Rotate Cube plugin in CCSM, but the changes were not applied. Also when I restart Compiz and CCSM, the setting goes back to disabled for Rotate Left/Right's button column. I also tried setting it in gconf-editor, but it didn't work either. My Compiz settings backend also happens to be using gcof.

So has anyone managed to get it working?

---

### Post by VirtualTiger on 2007-06-27
This is done in the Viewport Mouse Switch Setting, so make sure you have that enabled.

The default are:
```
Move Next -  Button5
Move Prev -  Button4
```

If you want Control Alt:
```
Move Next -  <Control><Alt>Button5
Move Prev -  <Control><Alt>Button4
```

---

### Post by hyperair on 2007-06-28
Well, obviously I've not made myself very clear. I was looking for something that allows me to do Ctrl+Alt+MouseWheel **anywhere in the screen**. This means I can put my cursor over an open window, and use that key combination and it will switch desktops. Is that possible?

---

### Post by VirtualTiger on 2007-06-28
Since it looks like you haven't figured it out yet, I just tried something different, so here's another solution that works when your inside another application.

Do the same thing I mentioned yesterday, just in the Rotate Desktop Cube plugin.

```
Rotate Left    <Control><Alt>Button5
Rotate Right   <Control><Alt>Button4
```

---

