---
title: "Nautilus Start Error"
date: 2006-12-25
forum: Desktop Environments
---

### Post by maddog39 on 2006-12-25
Hello all,

Okay so I reinstalled Ubuntu on my PowerBook after I majorly gunked up the last installation. But for some reason the new installation keeps acting up on me. GNOME will just randomly fail or crash for no reason and I have to restart to fix it as restarting X doesnt do anything. When other times it just works. But this morning I start up my computer and I keep getting this error, it told me previously that tons of widgets have failed in the panel and prompts to delete them, okay, I delete them. Now I continuously get this error at startup and even if I login via a "Failsafe GNOME" I still get the same error and more than half the applets fail. This really doesnt make any sense to since I've never had a problem anywhere neat like this in the two years I've been using Ubuntu. Also I'm using all built in applets and stuff, nothing custom. So I don't understand what problem is. If possible I'd like to restore GNOME without reinstalling everything.

Screenshot:
[http://www.dximages.uni.cc/files/1/screenshots/linux/nautilus_error.png](http://www.dximages.uni.cc/files/1/screenshots/linux/nautilus_error.png)

[Edit]
I think this solved my problem, temporarily anyway:
```

sudo aptitude reinstall ubuntu-desktop && shutdown -r now

```
All applets were still missing. But it boots fine and works atleast. :/

Thanks!
-maddog39

---

