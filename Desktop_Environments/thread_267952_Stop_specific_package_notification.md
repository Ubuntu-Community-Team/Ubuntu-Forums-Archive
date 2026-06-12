---
title: "Stop specific package notification"
date: 2006-09-29
forum: Desktop Environments
---

### Post by xpavement on 2006-09-29
I have compiled and installed my own version of the ffmpeg package, and the software notification icon keeps displaying wanting to update it, but I don't want that version installed. I tried "locking" the package in the package manager, but that didn't stop the update notification from appearing in my taskbar. I want to be notified of other updates, but not for this particular package. Is this possible?

---

### Post by mitch.c on 2006-09-29
> **xpavement said:**
> I have compiled and installed my own version of the ffmpeg package, and the software notification icon keeps displaying wanting to update it, but I don't want that version installed. I tried "locking" the package in the package manager, but that didn't stop the update notification from appearing in my taskbar. I want to be notified of other updates, but not for this particular package. Is this possible?

I think this will do what you want:
```
sudo aptitude hold packagename
```

---

### Post by xpavement on 2006-09-29
Thanks, I've just tried it, it didn't stop the notification from appearing, I had it do a "check", and it still would bring up ffmpeg as a package I needed to update, weird...

---

### Post by vjones777 on 2006-12-31
Excuse this as you've probably tried this already, but after you locked the package in Synaptic package manager (select package then Package->Lock version  - FYI for other new users who may read this), did you Reload?
I beleive that the selections arn't applied until reload is selected.

I just tried this for Wine which I didn't want to update (giving me shutdown problems) but I dont want to uninstall just yet either.  The orange icon became grey then went away.  Great.

Thanks for your post, I didn't  know about the lock feature until I found your thread!

Good luck.

---

