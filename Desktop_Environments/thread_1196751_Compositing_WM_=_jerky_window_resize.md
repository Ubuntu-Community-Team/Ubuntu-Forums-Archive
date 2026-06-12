---
title: "Compositing WM = jerky window resize"
date: 2009-06-25
forum: Desktop Environments
---

### Post by fela on 2009-06-25
Whenever I select a compositing window manager, such as compiz, or metacity with compositing enabled (gconf editor > apps > metacity > general > compositing manager), the action of window resizing appears jerky and slow, not smooth like it should be. However when I select a window manager with compositing disabled, it's just fine, nice and smooth like M$ Windoze (not that I like windows or anything :P). What could the matter be? I'm no developer so don't quote me on this, but my assumption would be that if you can make the window resize smoothly without compositing, what's stopping compositing managers from doing the same? Obviously if you have a little more knowledge about the coding of it all, then correct me if that's an absolutely absurd statement to make. But for now I'm gonna use metacity without compositing...

PS. All this is happening in GNOME, I haven't tried it in bloated KDE4 yet.

-Fela

---

### Post by jimv on 2009-06-25
Try this:

Install CompizConfig Settings Manager:

```
sudo apt-get install compizconfig-settings-manager
```

Then open it in System > Preferences >  CompizConfig Settings Manager

Click on General Options, and then the Display Settings tab.

Uncheck "Detect Refresh Rate" and move the slider for refresh rate to 100 (or type it in on the right).

Close the window.  Things should look much smoother now.

---

### Post by frmdstryr on 2009-06-25
nvm try that ^^^

---

### Post by fela on 2009-06-25
OK, thanks for the suggestion. I'll try it in a few minutes, when I've saved my Encore project in windoze.

PS. you don't need to tell me to install ccsm! I think compiz is pretty useless without it anyway. it's the first thing i did when i installed Linux (apart from fix the ttys resolution).

---

### Post by fela on 2009-06-25
OK, I tried what you suggested. It is more _bearable_, but it's still not comparable to either with compositing disabled or windows' wms (composited or not).

It can't be a limitation of all compositing, I can prove that by showing you a screencast of Vista's compositing manager (with smooth resize). The thing about Vista is that the rest of the OS completely sucks *** though, so that's why I use Linux!

Anyway it looks like I'll just have to live with it for the time being. It has been an issue ever since compiz existed, I believe - correct me if I'm wrong. :confused:

---

