---
title: "[nfs-client] Nautilus freezes"
date: 2006-04-14
forum: Desktop Environments
---

### Post by jchirac on 2006-04-14
I'm using Ubuntu 5.10 (fully up-to-date) on my laptop for a while now and I'm quite happy with it. I've had some problems, and solved most of them myself. Only, there's one anoying thing I can't solve. 

Well, whenever I mount a nfs share and browse it with Nautilus, Nautilus freezes up. It also takes the whole Xserver, or at least gnome, with it. Switching VC keeps working, and Ctrl+Alt+Backspace too. So, I tried to kill the Xserver, and start it again. Gnome doesn't want to load correctly (gnome-panel appears, but the desktop, and thereby probably Nautilus, doesn't) until I restart my computer.

Next thing I tried was to kill X, and kill nautilus and gnome-vfs-daemon etc. But that didn't help either. AFAIK, my logs don't output anything useful. I also can't find useful bug-reports at gnome.org. I can't run Nautilus in verbose mode as X freezes anyway when opening the share, so I can't see the console output.

Is this problem known to you guys? The problem is client-side as under Gentoo (on my desktop computer) I haven't got this problem. If it is a real bug, and not just my mistake ;-), I should file this bug, but I'm not sure.

Hope you can help me..

edit: **It's not just Nautilus, I was mistaking.** If I for example mount the nfs-share, and do ```
touch test
``` and then ```
cp test test2
```, that terminal or VC freezes.

edit2: /var/log/messages says "nfs: server x.x.x.x not responding", but the server's log gives no errors

---

### Post by jchirac on 2006-04-15
Anyone?

---

