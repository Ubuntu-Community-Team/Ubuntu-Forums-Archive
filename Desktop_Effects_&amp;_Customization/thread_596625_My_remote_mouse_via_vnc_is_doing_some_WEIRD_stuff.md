---
title: "My remote mouse via vnc is doing some WEIRD stuff"
date: 2007-10-29
forum: Desktop Effects &amp; Customization
---

### Post by diablo75 on 2007-10-29
I just finished with a remote session using VNC, having them start a reverse connection using x11vnc.

It's very hard to describe what was going on, but from the looks of it (and observations by the person on the other end), my mouse would look like it was a few inches to the right of where it says it is on my monitor.  The keyboard worked perfectly fine.  But the mouse just seemed to be all over the place, and that's never happened to me before.

They're using dual montiors, which is new to me via VNC, so just mentioning this in case it might have something to do with this.

---

### Post by krunge on 2007-10-29
Try adding the x11vnc option: ```
-xwarppointer
```  There seems to be a bug in the X server XTEST (mouse and kbd injection) when Xinerama (multi-heads) is enabled.

More info here: [http://www.karlrunge.com/x11vnc/#faq-xinerama]("http://www.karlrunge.com/x11vnc/#faq-xinerama") This was fixed upstream about a year ago: it should automatically apply -xwarppointer when it detects Xinerama on the display.

---

