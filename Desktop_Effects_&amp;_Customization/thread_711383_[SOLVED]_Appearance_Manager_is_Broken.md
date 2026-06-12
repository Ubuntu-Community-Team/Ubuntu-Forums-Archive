---
title: "[SOLVED] Appearance Manager is Broken"
date: 2008-02-29
forum: Desktop Effects &amp; Customization
---

### Post by okey666 on 2008-02-29
I am attempting to make my Ubuntu install look like 'Vista' to show the power of it to a friend. I have previously changed themes etc. but now whenever I attempt to install another theme the file dialogue comes up but seems to be constantly loading. Eventually I have to close it and then the entire appearance box freezes up until I restart.

 I followed [this post]("http://ubuntuforums.org/showthread.php?t=641320") but with no luck, it could not find the packages suggested to be removed at the bottom. 

Any ideas? I am running gutsy with gnome.

---

### Post by FuturePilot on 2008-02-29
Try this
```
sudo apt-get remove --purge gtk-qt-engine
```

---

### Post by okey666 on 2008-03-01
Thanks, that fixed it.

---

### Post by nynoah on 2008-04-15
cool this just helped me solve my problem.....got to love the forums.

---

