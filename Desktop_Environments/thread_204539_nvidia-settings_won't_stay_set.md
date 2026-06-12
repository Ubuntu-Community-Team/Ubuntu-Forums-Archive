---
title: "nvidia-settings won't stay set"
date: 2006-06-27
forum: Desktop Environments
---

### Post by Dragon_52 on 2006-06-27
I can use nvidia-settings successfully to correct a slight colour imbalance on my system. When I apply the changes everything is fine for a while. After the screensaver has activated, the settings are lost and I have to reapply them.

Any suggestions for making this a permanent fix?

---

### Post by flyingbrass on 2006-06-27
I was just struggling with the same thing.  Apart from the screensaver issue, settings aren't automatically restored after logging out and back in.  

Both problems seem to have been cured by adding this to start when initiating a gnome session.  (System -> Preferences -> Sessions -> Startup Programs)
```
nvidia-settings --load-config-only
```

I was surprised it also took care of settings getting lost each time the screensaver fired up.  I wonder if something like the suggestion in post #21 of [this thread](http://www.nvnews.net/vbulletin/showthread.php?t=61396&page=2) would also work.  I'm not sure where to put it.

---

### Post by Dragon_52 on 2006-06-28
Thanks a lot, flyingbrass - it seems to work fine now. 
Funnily enough, I had already discovered the *nvidia-settings --load-config-only* command, but didn't think to make it a startup item.

---

