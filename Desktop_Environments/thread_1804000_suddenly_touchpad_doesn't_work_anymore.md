---
title: "suddenly touchpad doesn't work anymore"
date: 2011-07-14
forum: Desktop Environments
---

### Post by Mappenz on 2011-07-14
Hi,

my touchpad worked out of the Box after insalling Xubunut 11.04 and did so ever since. But since yesterday it doesn't. It worked when i shut down the laptop and didn't when i booted later. How do i fix this? Yes i read the article about thouchpads. I don't think its a hardware problem.

---

### Post by Toz on 2011-07-15
Is there anything in /var/log/Xorg.0.log? Open a terminal window (Accessories->Terminal Emulator), type in the following, and post back the results:
```
cat /var/log/Xorg.0.log | grep -i touch
```

Also, have you tried resetting back to Defaults from Settings->Settings Manager->Mouse - select the Touchpad device and click on "Reset to Defaults"

---

### Post by Mappenz on 2011-07-16
My touchpad works again after i used fn + f7. Before you laugh at me, note: That of course was the first thing i tried it did not work back then. I did a few things in the meantime, i don't know what made the difference. Maybe its the same problem with my sound staying muted (and beeing resistent against the unmute button) after a reboot.

---

