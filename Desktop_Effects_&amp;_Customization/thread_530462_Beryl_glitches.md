---
title: "Beryl glitches?"
date: 2007-08-20
forum: Desktop Effects &amp; Customization
---

### Post by minulescu on 2007-08-20
Maybe I'm missing something, but this issue shouldn't be happening.

After rebooting my computer, beryl didn't come up autumatically. This might be expected. So I typed *beryl* and sure enough the desktop effects were visible, but when opening a window, I can't move it, and there is no minimize, maximize or close buttons. Having Beryl Manager open also seems to have an impact. When opening beryl-manager after bery it seems to disable beryl.. I'm not sure what the deal is. And I'm a noob with Ubuntu/Linux, so it might be something obvious that I'm missing. 
Thanks for any help.

---

### Post by luisromangz on 2007-08-20
You should start beryl manager first, it will care for start beryl correctly.

As for the missing title bar, maybe you are running beryl without a compatible window decorator (probable since you were starting beryl typiying just beryl in the command line). Or maybe you are running beryl with an Nvidia card and forgot to add th AddRGBGLXVisuals options in the xorg.conf file.

---

