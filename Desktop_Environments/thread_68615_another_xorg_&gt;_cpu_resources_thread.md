---
title: "another xorg &gt; cpu resources thread"
date: 2005-09-23
forum: Desktop Environments
---

### Post by farnsworth on 2005-09-23
Hey all,

I've been having what may be a rather unique problem, judging from the lack of anyone else complaining about it.  After I leave the computer on for a while, usually around 2 - 3 days, xorg will begin to suck the life out of my cpu: upwards of 50%.  No other processes need be running; top sez it's squarely xorg's problem.  There are no problems with the display (I've got the latest nvidia drivers running perfectly, and there's very little cpu spikage when I move windows).  Ive checked my logs, killed every backgroud process I could, even checked netstat (for rogue net processes), chkrootkit, clamav...  the only remedy I've found is restarting my session.

What Im running:  Latest official gdm, xorg, xfce packages(without gnome/kde services).  386 kernel on an Athlon 2100+ XP (might be the problem, but nvidia drivers don't like the 686 kernel).  firefox, XMMS & bittornado always on.

I've had this problem since switching to hoary 3 kernels, 2gdms, 2xorgs and 2xfces ago.  If anyone can help I'll be eternally grateful.

---

### Post by jworr on 2005-09-24
I had a similar problem and it was the gnome theme I was using.  I was using Yattacier 3 and it was using about 45% - 50% of my cpu.  I switched to clearlooks at it dropped to about 2%.  So it can make a big difference what window managers and such you are using.  I don't know much about xfce but it could be something similar.

---

### Post by farnsworth on 2005-09-24
Hi jworr,

    I had the same problem with gnome themes when I first got Warty.  I eventually switched to xfce because it's as barebones as possible; the fanciest desktop feature I'm using is a bit of transparency on my xterm.  I've  disabled gnome services, and stay away from any of the gnome utilities with too many 'automatic' features; automounting, etc., it's all just too unstable for my taste.
    However... I suppose it's possible that a cron'd process attempts to start gnome services, and it's giving xorg/xfce a headache.  But there's nothing in a 'ps aux' or 'top' that would hint at that, and it always begins when my computer is idle (I'm away and the screen's blanked).  If that were the case, though, I'd probably see something in my Xorg log(?)...

---

### Post by jworr on 2005-09-29
hmm possibly, use sudo /etc/crontab -e to look at your cron jobs

---

### Post by der_joachim on 2005-09-29
[QUOTE=farnsworth] (snip)  386 kernel on an Athlon 2100+ XP (might be the problem, but nvidia drivers don't like the 686 kernel).[/QUOTE]
Wouldn't you need the K7 kernel image for your Athlon? That's what my Athlon XP1800+ claims.

---

### Post by abbeychase on 2006-11-13
these threads confuse me.  my cpu is 100% idle except when I am building something.  that's weird.  you sure you don't mean your MEMORY??  your cpu should never be "running" unless you're doing something that requires it, like compiling something.  Now, as far as MEMORY is concerned, firefox is a memory HOG.  Closing it helps a lot, it's just an overbloated web-browser.  XMMS too.

So, if you notice that you have like 300 tabs open in FF, try closing some or closing it entirely.

---

