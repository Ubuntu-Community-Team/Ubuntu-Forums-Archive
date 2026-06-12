---
title: "Clock doesn't show on unity panel"
date: 2011-04-29
forum: Desktop Environments
---

### Post by leawning on 2011-04-29
Hi, I have upgraded to ubuntu 11.04 yesterday, but i found that there isn't any clock show on the top right side of the unity panel. I would like it to appear on the panel. How can i fix that? 

Thank you.

---

### Post by juliandidymos on 2011-04-29
Same problems here.  I could have sworn it was there on install, and then disappeared, I think, somewhere around the point where I changed my theme.

Clock and date both, gone.

---

### Post by leawning on 2011-05-02
Hi Julian, i found out that you need to install indicator-datetime from the software center, log-out and login again in order to have time and date shown on the top right corner. Enjoy. ^^

---

### Post by Frogs Hair on 2011-05-02
The clock applet was installed in Unity when I did a clean installation of 11.04 , but some who have done upgrades are missing the clock.

---

### Post by juliandidymos on 2011-05-02
Awesome; thanks.  That did the trick :)

I think I just went terminal with it, though -- my other issue is that my Software Center is no longer installing 100% of the time.  haha

If Ubuntu wasn't so awesome, I'd be complaining right now.

Anyway, I saw that post of yours (randomly), and saw the terminal code he ran, found out that mine wasn't installed and just ran:

```
sudo apt-get install indicator-datetime
```

LIke I said, did the trick ;)  Maybe I'll get the hang of this, after all...

---

### Post by juliandidymos on 2011-05-02
And I didn't upgrade, but I did install from *within* Windows.  But it was totally there when I first logged in the first few times, so unsure what happened.  Possibly somewhere in installs and updates, maybe?

---

### Post by voiger on 2011-11-01
You can simply press Alt+F2 and type 'unity --replace' and 'Enter' instead of log-out and log-in. Enjoy :)

---

### Post by clooch on 2013-04-06
Thanks, that did the trick

---

### Post by wildmanne39 on 2013-04-06
Thread closed. Please do not post in old threads.

---

