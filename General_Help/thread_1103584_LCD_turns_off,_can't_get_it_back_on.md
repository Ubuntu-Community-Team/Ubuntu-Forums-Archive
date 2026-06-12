---
title: "LCD turns off, can't get it back on"
date: 2009-03-22
forum: General Help
---

### Post by slogged on 2009-03-22
Hello geniuses. Thank you for taking the time to help me.

I converted a laptop into a wall mounted picture frame. Everything works great. BUT after about an hour or so the LCD turns off. I am able to connect just fine by VNC and SSH. Rebooting it bring the display right back for another hour, then it shuts off again. It is able to sit with the BIOS screen on for four hours (tested this), so it is something with Xubuntu and not the hardware.

I've disabled the event for the close lid button, power settings in BIOS & in Xubuntu are set not to turn the display off. 

Do you have something that I can try? Thank you

---

### Post by KeyserSoze93 on 2009-03-23
I have a slideshow set up with the Fluxbox window manager, and I have the following in the startup file:

```

xset -dpms
xset s off

```

This should disable any power saving and screensavers etc.

---

### Post by slogged on 2009-03-23
Thank you for the suggestion but unfortunately it didn't work. The display still turns off and there's no way to get it back on.

Is there anything else I can try?

> **KeyserSoze93 said:**
> I have a slideshow set up with the Fluxbox window manager, and I have the following in the startup file:

```

xset -dpms
xset s off

```

This should disable any power saving and screensavers etc.

---

