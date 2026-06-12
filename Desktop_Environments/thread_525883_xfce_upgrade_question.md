---
title: "xfce upgrade question"
date: 2007-08-14
forum: Desktop Environments
---

### Post by kystorms on 2007-08-14
i see that there is a newer version of xfce out now, my question is, how can i upgrade my version running now? Is it only via a downloaded cd iso, or can i do so with terminal, and if so, is there a how to  to follow?

:confused:
thanks

---

### Post by mojoman on 2007-08-23
If you're using Feisty and the standard repositories you have to Xfce 4.4.0 and *if* you want to use 4.4.1 (i.e. the latest version) you would have to either (1) add a repository in your /etc/apt/sources.list or (2) install manually with tarball or .deb. Personally, I'm lazy and tend to stick with what's in the standard repositories but occasionally I install other stuff and when I do, I'm very particular about the repositories I use and therefore tend to go with .debs. However, Xfce is a metapackage so you might have a bit of a problem getting a .deb but the version you want is in the Debian testing repositories (though I personally wouldn't mix Feisty, based on Etch, with Sid...).

Hope this helps
mojoman

---

