---
title: "Zaz crashes in Xfce"
date: 2012-09-07
forum: Gaming &amp; Leisure
---

### Post by Buntu Bunny on 2012-09-07
Zaz crashes after a couple of levels when I play it from Xfce. This doesn't happen in Gnome or Unity. Is there a way to fix this or is it something I have to live with? Do some games do better in certain DEs than others?

I asked about this in gaming and leisure, but I'm really needing help so perhaps it's more of a support question(?). I didn't get any replies there, so I'll ask in general help. I hope that's okay. 

My problem is that the game Zaz crashes after a couple of levels when I play it from Xfce. This doesn't happen in Gnome or Unity. Is there a way to fix this or is it something I have to live with? Do some games do better in certain DEs than others?

---

### Post by Toz on 2012-09-08
I've merged the two threads together. Please don't create duplicate posts.

As for the issue, try running zaz from the command line and when it crashes, post back any error messages that you get. 

Are all of these DEs on the same computer?

---

### Post by Toz on 2012-09-08
I just installed the game to have a look and yes, it does crash under Xfce with a segmentation fault but not under my other DE (awesome). I found that if I disabled the compositor in Xfce (Settings Manager -> Window Manager Tweaks -> Compositor Tab), then the game works fine. Perhaps you can create a bug report against the game:
```
apport-bug zaz
```

---

### Post by Buntu Bunny on 2012-09-08
> **Toz said:**
> I've merged the two threads together. Please don't create duplicate posts.

Toz, thank you and I apologize. I got to thinking perhaps this category was for discussing games in general, strategy, etc. rather than support. 

> As for the issue, try running zaz from the command line and when it crashes, post back any error messages that you get.

```
leigh@leigh-CM1740:~$ zaz
Segmentation fault (core dumped)

```

Obviously this is the same as you. 

> Are all of these DEs on the same computer?

Yes, all the DEs are on the same computer. I usually play from the menu rather than command line, and always send off the error report. 

>  I found that if I disabled the compositor in Xfce (Settings Manager -> Window Manager Tweaks -> Compositor Tab), then the game works fine.

Thank you! I will give this a try.

---

