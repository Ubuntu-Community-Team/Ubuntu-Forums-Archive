---
title: "Compiz Fusion Problems"
date: 2007-09-23
forum: Desktop Effects &amp; Customization
---

### Post by StarMcJustice5 on 2007-09-23
I just finished up this tutorial on how to install compiz-fusion, and in the end it worked, except that i couldn't get it to install the extra plugins or unofficial plugins.  I keep getting command not found.  Any help?

[http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/](http://kevin.vanzonneveld.net/techblog/article/enable_compizfusion_in_ubuntu_feisty/)

- go easy on me (no big words) i've only been on ubuntu for the last 10hrs :)

---

### Post by Happy_Man on 2007-09-23
Ah, Trevino's repos. I use those. :D

The command to install Fusion is: ```
sudo apt-get install compiz compiz-core compiz-fusion-plugins-* compizconfig-settings-manager libcompizconfig-backend-gconf
```

That should do it. If it doesn't, post the errors here.

---

