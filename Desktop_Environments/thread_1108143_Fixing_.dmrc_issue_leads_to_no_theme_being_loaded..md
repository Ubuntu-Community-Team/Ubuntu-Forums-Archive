---
title: "Fixing .dmrc issue leads to no theme being loaded."
date: 2009-03-27
forum: Desktop Environments
---

### Post by MBro on 2009-03-27
My .dmrc was being ignored by gnome upon logging in.

I did a google search and found [this site.]("http://mihirknows.blogspot.com/2008/06/homedmrc-file-is-being-ignored-solved.html".)  Which gave me these instructions.
```
sudo chmod 644 /home/xx/.dmrc
sudo chown xx/home/xx/.dmrc
sudo chmod -R 700 /home/xx
sudo chown -R xx/home/xx
```

The .dmrc issue is gone but now my theme won't load and it goes to the gnome default.  When I try to open the appearance manager the screen flashes black then logs me out.  I assume those instructions created a permission issue, but on which file I do not know.

---

