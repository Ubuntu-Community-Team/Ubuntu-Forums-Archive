---
title: "But I don't want to upgrade pan"
date: 2005-09-09
forum: Desktop Environments
---

### Post by [censored] on 2005-09-09
Hi. I deliberately downgraded pan newsreader to version 0.13.0, because the later version that came with Hoary had all sorts of nasty bugs that made it difficult to use my news server.

Now I'm stuck with a "You have 1 update available" icon in my system tray. How do I tell the package management system that I don't want to upgrade pan, and to stop telling me I need to?

---

### Post by rafakl on 2005-09-09
Double click the tray, and unselect the package.

---

### Post by [censored] on 2005-09-11
Tried that rafaki. Dun work. Little upgrade icon abnoxiously refuses to go away.

I've fixed it though, by compiling my own build of pan 0.13.0 from source, converting it to deb using checkinstall, and naming the package "oldpan". My apt-get repositories may have an update available for a package called "pan", but not  "oldpan".

---

