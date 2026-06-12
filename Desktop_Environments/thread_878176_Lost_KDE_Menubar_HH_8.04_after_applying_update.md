---
title: "Lost KDE Menubar HH 8.04 after applying update"
date: 2008-08-02
forum: Desktop Environments
---

### Post by ronc55 on 2008-08-02
I have KDE Hardy Heron on an HP AMD 64 bit.  I have religiously updated my installations as I receive notices that there are new ones out there.  This morning 08/02/08, I received and applied the two new ones that were made available.  Rebooted my computer this afternoon and lost my KDE Desktop.  I really would like to get it back?  Any suggestions?  All I can see is some icons for downloaded files and I'm running the default screen saver pointed at some of my pictures, that is running correctly.  I cannot see any of the customary menu's.  Firefox was running when I rebooted and I am able to use it.

---

### Post by Shmifty on 2008-08-02
> alt+f2
pkill kickerthen run> kicker
Hopefully the menubar (kicker panel) will appear.

---

### Post by ronc55 on 2008-08-02
That did it - it reappeared but lasted about 4 seconds and went away again.  I can replicate your process and it again lasts about 4 seconds.  Any further suggestions?

---

### Post by Shmifty on 2008-08-02
Which kernel and version of KDE are you running? (may help find a solution)

---

### Post by ronc55 on 2008-08-02
I am running 2.6.24-19 generic Kubuntu

---

### Post by ronc55 on 2008-08-02
I forgot to say in my last reply that it was the 664 bit version.  Also, I did have an one inch blank strip down the right side of my display that appeared when the kicker failed.  I have a full screen now by not running "kicker" again.  If I run kicker, the blank strip reappears.

---

### Post by ronc55 on 2008-08-03
OK - new day 08/03/08 - I found that KDE was upgraded and released on 7/30/08 and apparently has been applied to my system.  It obviously broke something.  How do I uninstall the update or if that is not possible, how can I move over to a GNOME desktop that works?

---

### Post by ronc55 on 2008-08-03
I noted that after I used pkill kicker from the command prompt, the desktop was almost normal, i.e., the one inch panel on the right of the screen disappeared, the if I used "kicker" the kicker panel would reappear for about 2 or 3 seconds and disappear.  I tried it one more time, and right mouse clicked on the "K", I got the panel to remain and I selected "Panel Menu". "Panel Configuration".  From there I turned off the "Hide Automatically" and selected "Only hide when a panel-hiding button is pushed".  Now "Kicker is available all the time.  Not sure I like that and will try other settings but for now I know how to get it to reappear.

So for my purposes, this tread is closed.  Thanks  Smifty for the "pkill kicker", kicker suggestion.  It did lead to a solution.

---

