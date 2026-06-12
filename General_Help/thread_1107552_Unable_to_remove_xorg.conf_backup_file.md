---
title: "Unable to remove xorg.conf backup file"
date: 2009-03-26
forum: General Help
---

### Post by yergeht on 2009-03-26
By saving new settings in my nvidia x-server settings. I try to save  the new settings and it gives me the message :unable to remove the old backup file for xorg.conf, don't know why that should matter... unless it's trying to overwrite the backup file, making recursive backup files, IDK, either way I'm wondering if I can just delete the old xorg.conf.backup file, so that a new one can be written.


The underlying problem here is that when my computer boots up my screen resolution is 1600+1200, after I log in, the screen gets re-drawn and it's redrawn at a less respectable 1024*768 so If either problem can be fixed,  awesome. I'm hopin I'll be able to just change the xorg.conf, but I still wanna know If I can delete the old backup file first... or if something else is actually goin on...

---

### Post by karlr42 on 2009-03-26
You have to run that nvidia settings program as root, it annoys me all the time..
```
sudo nvidia-settings
```

---

### Post by yergeht on 2009-03-27
Thank you... it's all good now!... I'll now if it's really fixed when I reboot

---

### Post by Slim Odds on 2009-03-27
> **karlr42 said:**
> You have to run that nvidia settings program as root, it annoys me all the time..

You are easily annoyed. It's that way for you own protection.

---

### Post by SuperSonic4 on 2009-03-27
> **yergeht said:**
> Thank you... it's all good now!... I'll now if it's really fixed when I reboot

You can just reset X by pressing ctrl+alt+bkspace

---

### Post by Slim Odds on 2009-03-27
> **SuperSonic4 said:**
> You can just reset X by pressing ctrl+alt+bkspace

That's a nasty way to handle it.

It's better to restart the X display manager from a console (Ctrl-Alt-F1).```
sudo /etc/init.d/gdm restart
```

Also, in the next release (Jaunty) that will not work by default.

---

