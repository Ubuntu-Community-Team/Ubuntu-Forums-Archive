---
title: "Need Chromium for Gnome Extensions, But Won't Run"
date: 2017-10-21
forum: Desktop Environments
---

### Post by wmichaelb2 on 2017-10-21
I installed 17.10 yesterday, and opened extensions.gnome.org to tweak the desktop. I installed Gnome Shell Integration, but got an error message that stated that native host detector was not running. On investigation, I found that Firefox no longer supports some standard that is needed. The link to manually install it in Firefox led to directions on how to install it in Chromium. So I installed Chromium from the software manager, but it won't open. Aaarrggh! How do I get a good install of Chromium? Thanks in advance.

---

### Post by mc4man on 2017-10-21
It's not chromium you need & firefox will work fine with the plugin.
you need to install this package
```
sudo apt install chrome-gnome-shell
```

---

### Post by wmichaelb2 on 2017-10-22
mc4man: that worked, you're two for two. Thanks again so very much!

---

