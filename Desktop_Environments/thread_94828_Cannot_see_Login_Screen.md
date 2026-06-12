---
title: "Cannot see Login Screen"
date: 2005-11-24
forum: Desktop Environments
---

### Post by shikamaru5314 on 2005-11-24
Hi,

I have a prob.

First I install Hoary with monitor that support 1024x768. Everything work fine.

Then I switch to older moniitor that support   800x600 and below. Then I cannot see the login screen. I succesfully manage to change screen res to 800x600 on desktop but not on  login screen . So how to solve this prob?

---

### Post by bernardfrancois on 2005-11-25
Is it only the log-in screen which you can't see or does your monitor kinda 'turn off' after X Window System started?

If you don't get any image at all, something must be wrong with your display settings. Maybe you can try an even lower resolution first (640x480). I'm currently having probs with a screen as well, it only seems to work at 640x480...

---

### Post by shikamaru5314 on 2005-11-28
Its only on the login screen. The X window itself is okay

---

### Post by bernardfrancois on 2005-11-29
You mean you log on in text mode and then you have to start X Window System manually? Or does it log you on automatically?

Anyway, normally you can set options for the login screen by running **gksudo gdmsetup** . There's also an option to log on automatically, which might be set to log on automatically after showing the log on screen for 0 seconds...

---

