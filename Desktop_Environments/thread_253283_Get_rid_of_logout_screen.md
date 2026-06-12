---
title: "Get rid of logout screen?"
date: 2006-09-08
forum: Desktop Environments
---

### Post by nekr0z on 2006-09-08
Hello there!

I would like to get rid of logout screen. I mean, when I press a power button on my laptop, I want the system to suspend-to-disk immediately, not to show me a screen. Is there a way to do it, and where can I read how to go this way?

Thanks in advance.

---

### Post by hw-tph on 2006-09-08
Start **gconf-editor** from a terminal and go to /apps/gnome-power-manager. Click the action_button_power key in the right frame and read the info below. You can set the value to "suspend" (without the quotes, of course) to make it suspend.


Håkan

---

### Post by nekr0z on 2006-09-08
This is just that, thank you! Your answer is a number one in being rapid, strict and useful among all the answers I ever received on Ubuntu Forums. Thanks a lot again!

---

