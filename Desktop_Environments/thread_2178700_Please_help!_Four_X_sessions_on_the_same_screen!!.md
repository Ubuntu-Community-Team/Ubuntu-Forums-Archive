---
title: "Please help! Four X sessions on the same screen?!?!"
date: 2013-10-04
forum: Desktop Environments
---

### Post by jmborr2 on 2013-10-04
This is the disaster I've run into (look at the clock)  :(
[ATTACH=CONFIG]246755[/ATTACH]
It looks like I have four X-sessions running on my screen. Everything started when I added a second monitor and plugged it to my second video card. After fidgeting with the "NVIDIA X Server Settings" I ended up with this sorry situation. Right now I have unpluged the second monitor and I am back to one monitor, one video card.
My question is: what steps do I have to take to get back to get rid of the X-sessions? I don't even know if these are extra X-sessions or what.

I tried reconfiguring the xserver
```
sudo dpkg-reconfigure xserver-xorg
```
but this doesn't help. In fact, it seems I don't need and xorg.conf file in order to start an X-session!

I'm at a loss. Any help is immensely appreciated.

---

### Post by deadflowr on 2013-10-04
Doesn't nvidia xserver settings panel(the gui) have a reset to defaults option?

---

### Post by jmborr2 on 2013-10-04
Thank you! I did that and I also removed gnome classic. Things were fine in Unity. Now I think I'm back to normal

---

