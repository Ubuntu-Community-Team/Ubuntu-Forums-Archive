---
title: "Switching Consoles + Compiz = Crash"
date: 2007-10-22
forum: Desktop Effects &amp; Customization
---

### Post by mb108 on 2007-10-22
After I switch to console mode (CTL+ALT+F#), when I try to return to the desktop it doesn't come up properly. I can see the mouse and move it, but the background is black except for a bar at the bottom that comes up as "static" ([like this]("http://mywebpages.comcast.net/orb/output.html")). Keyboard input may or may not be dead. If dead, I can't CTL+ALT+Backspace or switch back to console. Only thing I can figure is reboot. :confused:

This only happens when Compiz is enabled, if I do "metacity --replace" I can switch around with no problems.

Any ideas?

---

### Post by torturedutopian on 2007-10-23
Same issue here : ubuntu gutsy x86, nvidia 8600 gts.

Actually, I noticed it when trying to launch a second X server for some games or TV output that don't work properly with compiz, and noticed exactly the same symptoms appeared when using the fast user switching applet.

Any idea ? :-/

---

### Post by torturedutopian on 2007-10-23
Hmm... Check the recently release nvidia beta drivers.. :)

[http://www.nvidia.com/object/linux_display_ia32_100.14.23.html](http://www.nvidia.com/object/linux_display_ia32_100.14.23.html)

"Fixed a problem with a Compiz after vt-switching."

---

### Post by mb108 on 2007-10-23
Yeah, I tested some more and the full crash happened more regularly when I ran an OpenGL game in the new X server.

Thanks for the link to the new drivers, I'll try it out. :popcorn:

---

