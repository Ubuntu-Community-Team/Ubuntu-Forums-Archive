---
title: "Restoring lightdm as default manager..."
date: 2013-05-31
forum: Desktop Environments
---

### Post by Baldrick_NZ on 2013-05-31
Hi all,

I have a fresh install of 13.04GS, which was installed via Unity. The thing is, every time I boot into Gnome, I get the blue screen with the familiar Gnome vertical 'Venetian blinds' before showing the lightdm log in screen. 

How can I revert to the traditional purple lightdm screen?

What files lightdm should I have installed?

Thanks in advance,
Baldrick.

---

### Post by MG&amp;TL on 2013-05-31
I think you're asking about how to use *lightdm* as the session manager, not *gdm*. (Sorry, been a while since I used GNOME). 

If I'm correct, run:

```
sudo update-alternatives --config x-session-manager
```

And pick your preferred choice from the list.

---

