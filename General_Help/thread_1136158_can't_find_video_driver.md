---
title: "can't find video driver"
date: 2009-04-24
forum: General Help
---

### Post by fbp90crx on 2009-04-24
I have a HP Pavilion 533w (old, I know..) and I just loaded Jaunty on it and it is running slower than when it had XP on it. I heard that not having the video driver could make everything run slow. The only problem is the only driver I have found was for XP and it is a .exe from [http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=pv-28391-1&lc=en&dlc=en&cc=us&product=90862&os=228&lang=en](http://h10025.www1.hp.com/ewfrf/wc/softwareDownloadIndex?softwareitem=pv-28391-1&lc=en&dlc=en&cc=us&product=90862&os=228&lang=en) . Will this work? or what should I do?

---

### Post by 3Miro on 2009-04-24
That is not how one installs drivers for Linux.

Most of the time, you don't have to worry about is. All the Intel Video cards that I have seen work out-of-the-box (i.e. just work, without you having to do anything).

Sometimes one deals with proprietary drivers and then you have to go to System -> Admin -> HW manager. Check to see if there are any drivers available there.

Also, what exactly is wrong? What exactly is slow?

---

### Post by fbp90crx on 2009-04-24
Anything in wine is very slow, takes a while to come up and load anything. Just opening programs like firefox takes longer than it did in XP. and some windows will just kinda studder. Like most everything is slower than expected I guess you can say.

---

### Post by 3Miro on 2009-04-24
OK everything in wine would be slower, especially on load (once it loads it is hardly noticeable). Why are you running FireFox under wine and not the Linux version?

What are the Linux native apps doing, Nautilus, the Linux Firefox, Gedit, Totem?

---

### Post by fbp90crx on 2009-04-24
No i meant linus firefox, I'm not trying to run it in wine.

---

### Post by 3Miro on 2009-04-24
Go to Applications -> Accessories -> Terminal and type
```

top

```
then press enter. You will be able to see if there is a rouge process that takes up a lot of resources.

---

### Post by fbp90crx on 2009-04-24
Doesn't look like anything is running rough. Xorg is using like 55% CPU, is that normal?
Like even sometimes when I type the words will lag and take a sec to catch up.

---

### Post by 3Miro on 2009-04-24
> **fbp90crx said:**
> Doesn't look like anything is running rough. Xorg is using like 55% CPU, is that normal?
Like even sometimes when I type the words will lag and take a sec to catch up.

Constant 55% for Xorg is bad. Xorg is the graphical environment. It can peak at high numbers sometimes, but overall should stay well below 10%. The problem is that you cannot shut down Xorg (it will stop all graphics).

Did you check the Hardware manager for drivers.

---

### Post by fbp90crx on 2009-04-25
Yes, it said no propietary drivers are in use on this system.

---

### Post by fbp90crx on 2009-04-26
Still having this problem, what should I do?

---

