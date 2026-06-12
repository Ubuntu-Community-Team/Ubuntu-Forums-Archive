---
title: "desktop effects + frostwire/limewire"
date: 2007-06-27
forum: Desktop Effects &amp; Customization
---

### Post by icenova on 2007-06-27
Sup guys, can anyone tell me how come i cannot use frostwire or limewire when i have beryl/desktop effects active?

frostwire just shows up as a white screen..

help?

---

### Post by ThrobbingBrain66 on 2007-06-27
Currently there are conflicts with Java/Swing apps and Compiz/Beryl
The following link has a fix for the problem.  It looks a little complicated, but it works.

If you don't have your terminal window large enough, some lines of code get split into two parts and then mess up the fix.  If you encounter any errors, make sure to check for this.

Good luck!

EDIT:
The lines that gave me trouble are listed below:

```
-                // Do the same for non-reparenting WMs (Compiz, Looking Glass)
+                // Do the same for non-reparenting WMs (Compiz, Looking Glass, Beryl)
```
and
```
-        return (XWM.getWMID() == XWM.COMPIZ_WM || XWM.getWMID() == XWM.LG3D_WM);
+        return (XWM.getWMID() == XWM.COMPIZ_WM || XWM.getWMID() == XWM.LG3D_WM || XWM.getWMID() == XWM.BERYL_WM);
```

---

### Post by icenova on 2007-06-27
thanks, but where is the link?

---

### Post by ThrobbingBrain66 on 2007-06-27
lol, sorry
[http://wiki.beryl-project.org/wiki/Java](http://wiki.beryl-project.org/wiki/Java)

---

