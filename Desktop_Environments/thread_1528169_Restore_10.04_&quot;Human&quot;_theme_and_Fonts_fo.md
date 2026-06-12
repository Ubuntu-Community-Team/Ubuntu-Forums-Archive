---
title: "Restore 10.04 &quot;Human&quot; theme and Fonts folder?"
date: 2010-07-10
forum: Desktop Environments
---

### Post by Coderoid on 2010-07-10
Hi all,

I have Ubuntu Lucid Lynx installed and thought I'd try out Mac4Lin. I then decided to remove it and ran the script for doing so. This worked, except that it seems to have removed one of the standard Ubuntu themes (Human) and left some Mac4Lin fonts in my fonts folder (can't say which they all are).

How do I repair my Ubuntu installation without upsetting my 3G internet access, etc? I don't have an ethernet connection, but am using Vodacom 3G.

PS: Can I do this from the Ubuntu disk?

Thanks

---

### Post by Steve603z on 2010-07-11
```
sudo apt-get install human-theme
```, then go into System > Preferences > Appearance and select the human theme again

as for the fonts, I'm not familiar with "Mac4Lin", but I would check Synaptic to see what packages with the name containing the word "font" exist, and look for a suspicious package in there

---

