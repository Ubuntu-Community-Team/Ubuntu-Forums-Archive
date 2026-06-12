---
title: "Desktop background not extending to second screen"
date: 2011-06-12
forum: Desktop Environments
---

### Post by complience on 2011-06-12
Background is not extending into my second monitor but the top taskbar and mouse do show.

The resolution is slightly out also but can't fix that right now

OS:
Ubuntu 32bit 11.04
Unity

Graphic Card:
Intel® GMA X4500

---

### Post by danopia on 2011-06-12
My Unity laptop is able to dualscreen with external monitors (mostly tested with projectors, and always with a res that doesn't match the main display). The problem is that Unity appears to not draw on the new desktop area until you reboot, which is specific to Unity as far as I could tell.

---

### Post by complience on 2011-06-13
Yes I agree

Although you only need to log the user out not fully reboot.

bug in unity

---

### Post by danopia on 2011-06-13
On my laptop, changing the virtual res didn't result in black -- it resulted in render errors; random Xorg buffers smashed together. It looked way more glitched.

And yes, I meant log out. I had to reboot when I was doing it because the button to log out was in the glitch area and I couldn't read the menu. Drawing anything fails in the glitch area.

---

