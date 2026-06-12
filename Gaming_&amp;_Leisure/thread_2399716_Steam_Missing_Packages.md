---
title: "Steam Missing Packages"
date: 2018-08-29
forum: Gaming &amp; Leisure
---

### Post by texaszeediot on 2018-08-29
So I'll be honest, I don't know much about Linux, my friend who's been using it for years is teaching me, but we're both out of ideas now. We "installed" Steam on both my Chromebook that has Ubuntu 16.04 on it and my Raspberry Pi which runs a form of Debian(which might have the same problem). They both say that libgl1-mesa-dri:i386, libgl1-mesa-glx:i386, and libc6:i386 are missing (packages needed to be installed) when we try to launch steam on them. We've attempted to run every command we've found and it didn't work. every time it just says that unable to be located. Any help would be appreciated and I also posted this on askabuntu - you can see that here [https://askubuntu.com/questions/1069952/steam-installation-failure-ubuntu-16-04](https://askubuntu.com/questions/1069952/steam-installation-failure-ubuntu-16-04)

---

### Post by wildmanne39 on 2018-08-29
Please use the default font color and properties unless you need to highlight or draw attention to a part of your post.

---

### Post by oldrocker99 on 2018-08-30
How did you install Steam? If you downloaded it from the Steam website, it just may be your problem. This has **always** worked for me:
```
sudo apt install steam
```

This will pull in every dependency, and it should run fine. Good luck!

---

