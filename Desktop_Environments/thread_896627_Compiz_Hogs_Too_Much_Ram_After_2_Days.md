---
title: "Compiz Hogs Too Much Ram After 2 Days"
date: 2008-08-21
forum: Desktop Environments
---

### Post by HotDogBunToo on 2008-08-21
[After experiencing this problem regarding my memory being hogged by some mysterious force]("http://ubuntuforums.org/showthread.php?t=859198") - I have started the process of narrowing down what it is.  

Turns out that after a few weeks with no issues whatsoever it's my Compiz (as evident by me not running Compiz for this time period) that winds up eating away my memory and soon I wind up with over 900 of my 1GB memory used up resulting in a machine that doesn't do anything right unless I was to restart x-server or reboot.  Everything is all good when I first start up but after 36-48 hours the hogging of my resorces is apparent - especially when I type in 'top' command and it shows Compiz chugging away at more then 60% of MEM%.  Even when I turn off Compiz and type in:
```
sudo echo 3 | sudo tee /proc/sys/vm/drop_caches
```
I still have to resort to hittin the backspace + ctrl alt to restart things and have memory freed up again.

So while I'm able to FINALLY have the bulletproof runtime without Compiz (I'm even able to have VirtualBox XP run for the past few days with no negative lag!! :))... fact is I really miss the neato effects and wonder if theres' a way to not have it hog my resources through memory leak after 48 hours.

---

### Post by kagashe on 2008-08-25
If your graphic card is nvidia there is a [bug report]("https://bugs.launchpad.net/ubuntu/+source/compiz-fusion-plugins-main/+bug/151168").

kagashe

---

### Post by Crafty Kisses on 2008-08-25
When compiz is running post the results of > top

---

