---
title: "Need help with CAJA update, but no MATE desktop!"
date: 2013-10-05
forum: Desktop Environments
---

### Post by WinRiddance on 2013-10-05
Hi all. Some time ago I installed the Caja file manager from the repositories after having installed Xubuntu. There are several reasons why I didn't want all of the Mate desktop, so finding Caja in the repos was fantastic for me. One of the main reasons why I use Caja is because of the instant "hover" preview for MP3 files ... super handy for making large compilations.

Well, my then installed Caja is version 1.2 and by now that's already changed twice, to the current version of Caja 1.6 which I would like to have as well. Can someone give me a step by step on how to upgrade Caja **without having to install the remainder** of the Mate desktop environment? I surely would appreciate it. Thank you.

.

---

### Post by Dreamer Fithp Apprentice on 2013-10-07
Go to mate-desktop.org. Follow the instructions you'll find somewhere on that site for adding the repository appropriate for your distro. ```
sudo apt-get update
sudo apt-get install caja
```That's all. I would expect it to install a newer version if one is available and do nothing otherwise. Except maybe for a few dependencies it won't install anything you don't tell it to. And it will warn you what it is going to install anyway before you accept. Even if for some reason you DID install the whole shebang, which if you don't want it there is no reason to, you still wouldn't have to use it. You still get to select what DE you want to boot into at the login screen. You can boot into unity or lxde or cinamon or openbox or whatever and still use caja from the DE you like.

---

### Post by WinRiddance on 2013-10-08
Thanks for the assist. I went ahead and stumbled upon this other thread which related to what I was trying to do. Spared me the whole hassle of installing the entire desktop environment of Mate. I really can't stand the fact that I end up with oodles of double entries in my Menus & Startup Applications. Drives me nuts ... especially since some of the duplicates have identical names which makes it even more confusing to remove the ones that you don't want. It's something that the Mate developers really needed to get a handle on, ever since the 1st release of Mate ...
Anyway, here's that link: [http://forums.linuxmint.com/viewtopic.php?f=206&t=144546&p=772274#p772274](http://forums.linuxmint.com/viewtopic.php?f=206&t=144546&p=772274#p772274)

.

---

