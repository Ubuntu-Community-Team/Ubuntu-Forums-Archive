---
title: "Can't get rid of Flash 9!"
date: 2010-05-30
forum: Desktop Environments
---

### Post by RembrandtQEinstein on 2010-05-30
Even after I install Flash 10, when I go into Firefox (3.6.3 on Ubuntu 10.04), Firefox runs Flash 9. Videos, such as youtube, work but have no sound. In Firefox, tools->add ons->plugins, it says Shockwave Flash 9. 

I have removed and reinstalled Flash several times. I have used the Linux installer and the Adobe installer. I have manually copied the libflashplayer.so file. But still it is Flash 9.

I can get it to work by disabling Flash from within Firefox (tools->add ons->plugins) exiting Firefox, reinstalling Flash using the Linux installer (or manually copying libflashplayer.so) then restarting Firefox, then reenabling the Flash 9 plugin (ie tools->add ons->plugins). It actually is then, and only then, using Flash 10. Sounds works too! But when I restart Firefox, it is using Flash 9 again.

How do I get rid of Flash 9 permanently?

Thanks

---

### Post by RembrandtQEinstein on 2010-05-30
I have wrestled with sound and flash and flash version for hours and hours. Turns out there was a plugin installed in my home directory.

~/.mozilla/plugins

I never saw that because after you install the Flash 10, the path says it is /usr/lib/flashplugin-installer/libflashplayer.so however it runs the plugin from ~/.mozilla/plugins

Frustrating but I finally have Flash 10 and sound at the same time :)

---

### Post by lovinglinux on 2010-05-30
Next time use [FLASH-AID](http://flash-aid-extension.blogspot.com) extension for Firefox. It will remove conflicting plugins (including the one that was causing your problem) and install the proper flash version according to your browser architecture.

---

### Post by RembrandtQEinstein on 2010-05-30
I will try that first next time

Thanks!

---

