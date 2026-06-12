---
title: "no menus or taskbar"
date: 2009-02-03
forum: Desktop Environments
---

### Post by ledererster on 2009-02-03
I changed some graphics options, and now when I boot my computer up and log in, only the desktop shortcuts come up. No menu on top or taskbar. How can I fix this?

I'm using ubuntu 8.10.
Thanks!

---

### Post by wstout on 2009-02-03
Might want to take a look here [http://www.saifur-rahman.com/2008/12/restoring-default-ubuntu-panel/](http://www.saifur-rahman.com/2008/12/restoring-default-ubuntu-panel/) this will reset everything back to the default and restore your panels. That is if the panels disappearing are your problem, since you said you changed some graphics options it would probably be helpful to know what you changed, before you try anything.

---

### Post by ledererster on 2009-02-03
I was messing with some dual display options. It wanted me to reboot and when I did, it was only on the one monitor still and only had the desktop icons.

---

### Post by wstout on 2009-02-03
Oh ok I'm betting that may be the culprit then. If you know how to see if you can reverse the settings on the dual display, reboot and see if that helps out. Dual displays are a pain in the rear sometimes. If that doesn't work you may need to come back armed with what graphics card you have, and it may require you to reconfigure your X settings.

---

### Post by UbuntuNerd on 2009-02-03
wstout the solution from the link you offer does not longer work, just try deleting one of your panels and then use the code you'll see what I mean. here is the new solution no reboot require:
```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

```

---

### Post by wstout on 2009-02-03
UbuntuNerd, thanks for the correction, I will update that its been a while since I erased my panels that worked a while back :) I'm afraid that's not really the problem lederester is having anyway... hope that didn't mess him up more.

---

### Post by UbuntuNerd on 2009-02-03
you might be right his problem might be something different, he could still try the code it could work.

---

### Post by ledererster on 2009-02-03
I got it figured out. I went into recovery mode and fixed the X server I think it was. Thanks for you help.

---

