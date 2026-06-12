---
title: "Hot Corner for &quot;Scale Windows&quot; in 12.10?"
date: 2012-11-02
forum: Desktop Environments
---

### Post by nitroguy on 2012-11-02
Hey!

After the upgrade to 12.10, it took away my Compiz, and from what I understand, even if I were to download Compiz, it doesn't work right with 12.10. I'm fine with that (wobbly windows didn't have that much impact on how I work, after all), but the one thing that's (almost) a deal breaker, is "Scale". You know, "Super+W". I had a hot corner set up that worked great in my work flow, but it's gone.

Anyone know how to reinstate my Scale hot corner in 12.10?

Thanks!

---

### Post by stinkeye on 2012-11-02
> **nitroguy said:**
> Hey!

After the upgrade to 12.10, it took away my Compiz, and from what I understand, even if I were to download Compiz, it doesn't work right with 12.10. I'm fine with that (wobbly windows didn't have that much impact on how I work, after all), but the one thing that's (almost) a deal breaker, is "Scale". You know, "Super+W". I had a hot corner set up that worked great in my work flow, but it's gone.

Anyone know how to reinstate my Scale hot corner in 12.10?

Thanks!
In Quantal if you see unity your running compiz.
> After the upgrade to 12.10, it took away my Compiz
Do you mean compizconfig-settings-manager (ccsm) ???
Install and set up scale as you did before in ccsm > scale > bindings
Enable the Scale Addons plugin for extra features like middle click to close window.
```
sudo apt-get install compizconfig-settings-manager
```

Compiz works the same for me in 12.10 as 12.04 minus a couple of 
animation effects no longer included like burn.

---

### Post by nitroguy on 2012-11-02
Thanks Stinkeye. I guess you're right, it took away CCSM, but not necessarily Compiz. I'll reinstall ccsm.

Thanks! Glad it was so simple!

---

