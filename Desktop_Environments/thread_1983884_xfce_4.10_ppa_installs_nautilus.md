---
title: "xfce 4.10 ppa installs nautilus?"
date: 2012-05-20
forum: Desktop Environments
---

### Post by eddier on 2012-05-20
Installed xfce 4.10 from the PPA outlined in Webupd8.

Opened up my file manager and smiled because the Thumbnails were much bigger.

Then strange things started happening on the desktop,resize handles wern't working and other weird things. Thats when I discovered I was using Nautilus.

I cant remove it because Synaptic wants to remove Ubuntu Studio desktop etc.

I've managed to swap back to Thunar-but i am still puzzled as to how Nautilus got there in the first place!

eddie:-k

---

### Post by rai4shu2 on 2012-05-20
ubuntustudio-desktop: still depends on nautilus. <-- there's your problem right there

Bottom line: if you want to remove nautilus, you'll need to remove ubuntustudio-desktop along with it. No big deal, really. All those "desktop" packages are just meta packages (for if you want to do a nicer, smoother distribution upgrade a year or so from now).

---

### Post by vasa1 on 2012-05-20
> **rai4shu2 said:**
> ubuntustudio-desktop: still depends on nautilus. <-- there's your problem right there

Bottom line: if you want to remove nautilus, you'll need to remove ubuntustudio-desktop along with it. No big deal, really. All those "desktop" packages are just meta packages (for if you want to do a nicer, smoother distribution upgrade a year or so from now).

I installed 4.10 (from [https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10](https://launchpad.net/~xubuntu-dev/+archive/xfce-4.10)) over 4.8 which I installed from USC onto vanilla Ubuntu 12.04. Nautilus is obviously present but doesn't cause me any problems. That maybe because I'm not, intentionally or accidentally, running any software that deems fit to invoke nautilus. And, yes, I've read that nautilus can cause issues during an Xfce session.

But I'm not at all sure that it is necessary to _remove_ nautilus.

---

### Post by eddier on 2012-05-21
THank-you for the replies.):P

I wasnt aware Nautilus was part of Studio,that being the case I'm baffled as to why it decided to replace Thunar without any (apparent) prompting from me!

It was nice to have big thumbnails for a while-ah well, wheres my spectacles.

eddie

---

