---
title: "Show Contents while resizing a window? 9.10"
date: 2010-01-24
forum: Desktop Environments
---

### Post by teraploppy on 2010-01-24
Greetings!  I've been clawing through the forums and FAQ's..  Can't find out how.

Anyone know the trick to getting Ubuntu to show the contents of a window while I resize it?  It WAS doing this until I loaded up the drivers for my Nividia Quador 135M (works great!)  I'm very happy with my Ubuntu 9.10, I even have all the bouncy window effects running. 

Still, I would love get rid of the "faded blue resizing box" and see the contents instead.  Anyone know?

---

### Post by stinkeye on 2010-01-25
ccsm > window management > resize window > general > default resize mode > normal

---

### Post by teraploppy on 2010-01-25
**STINKEYE!** :KS

You are a Golden God!  Thank you.   It took me a moment to figure out that "CCSM" meant Compiz Configuration Setting Manager, but after that I was able to look it up and find out more.

I installed it using this command:

```
sudo apt-get install compizconfig-settings-manager compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-plugins emerald
```

All this information can be found on the Ubuntu forums [HERE]("http://www.ubuntugeek.com/how-to-install-and-configure-compiz-fusion-in-ubuntu-9-10karmic.html")  :popcorn:

---

### Post by Jetro on 2010-12-08
How can I turn OFF content showing when resizing Windows? I don't have Compiz installed at the moment, so I wonder. ^^

---

### Post by stinkeye on 2010-12-08
Can't find a specific setting for this in Metacity but enabling
**gconf-editor /apps/metacity/general/reduced_resources**
will draw wire frames intead of the window contents while resizing.
It also changes a couple of other things though.

---

### Post by Jetro on 2010-12-09
Hey, thanks, you!
That option creates a hideous grid, but at least it was what I was looking for. :)

Isn't it weird that show content while resizing window is enabled by default, and disabled when you install fancy compiz effects? It's like the opposite of Windows.

---

### Post by Decatf on 2010-12-09
Normal resizing on Compiz can result in all kinds of hideous crashing on some setups. Every <=r500 radeon card I've tried has had disastrous results with normal resize.

---

### Post by wpurcell on 2012-01-17
Yes, and thank you "From the Future"!

---

