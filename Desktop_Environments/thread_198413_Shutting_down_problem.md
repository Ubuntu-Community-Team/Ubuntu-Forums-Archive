---
title: "Shutting down problem"
date: 2006-06-17
forum: Desktop Environments
---

### Post by viraptor on 2006-06-17
I've got a problem with shutting down system. I select shut down in gnome and then Xs are not responsive (can't click anything), but it just stays like this. When I switch to console then, login and do `shutdown`, it closes all daemons and shuts / powers down without any problems.
How can I check, why it hangs? What exactly is run after selecting shut down in menu?

---

### Post by rumli on 2006-06-17
Could your problem be related be related to [this]("http://ubuntuforums.org/showthread.php?p=1106454#post1106454")?

I had a similar problem (machine hangs with a blank screen upon reboot/shutdown/switch-to-console/gdm restart), which went away when I disabled USplash according to [this suggestion]("http://ubuntuforums.org/showthread.php?p=1106454#post1106454").

To disable USplash, edit your /boot/grub/menu.lst file by:
```

sudo gedit /boot/grub/menu.lst 

```
and remove the "splash" word from the line that looks like
```
kernel          /boot/vmlinuz.... ro quiet splash
```

When you next boot, the brown booting information will be replaced by plain black and white text, so don't be dismayed by that. :)

---

### Post by viraptor on 2006-06-17
I don't think so - when doing shutdown from console I still see splash without any problems. Box doesn't hang up too - it's just that X server becomes not responsive - I can kill it and start it again without problems, so it doesn't get to swiching init state.
Also - it sometimes works - like 1/20 chance, but it seems random - I can't find relation to any program.

---

