---
title: "Netbook Remix Help"
date: 2009-01-09
forum: Desktop Environments
---

### Post by Mr. Mulder on 2009-01-09
Hi,

I'm running ubuntu 8.10 netbook remix on a Dell Mini 9, just installed netbook remix and its not running very smoothly...

[http://img205.imageshack.us/img205/9765/screenshotkh5.png](http://img205.imageshack.us/img205/9765/screenshotkh5.png)

if you take a look at that screenshot, when i open an app like firefox, it reveals its self in chunks or not at all, its really clunky ...same happens when i try to open pidgin or anything else.

also, the top main bar never shows in fullness, say if i hover my mouse over where the time and date should be in the top right, it will reveal in sort of chunks where as the rest of that bar will just show as the human background. i'd just as sooner get rid of the top bar all together and just use the netbook remix interface but that wouldn't solve the problem of apps not behaving right...

edit: another example [http://img518.imageshack.us/img518/7112/screenshot3cu1.png](http://img518.imageshack.us/img518/7112/screenshot3cu1.png)

---

### Post by AnRa on 2009-01-09
If you have the visual effects (i.e. Compiz) enabled you should try disabling them.

---

### Post by ugm6hr on 2009-01-09
> **AnRa said:**
> If you have the visual effects (i.e. Compiz) enabled you should try disabling them.

I agree - this looks like a Compiz issue (note transparency on screenshot).

I'm sticking with the default 8.04 on my Mini9.

---

### Post by Mr. Mulder on 2009-01-09
i followed these instructions [http://www.ubuntumini.com/2008/11/stop-compiz-fusion-from-loading.html](http://www.ubuntumini.com/2008/11/stop-compiz-fusion-from-loading.html) - to stop compiz from loading, is this not enough to solve it as the problem is still occurring?

---

### Post by ugm6hr on 2009-01-09
> **Mr. Mulder said:**
> i followed these instructions [http://www.ubuntumini.com/2008/11/stop-compiz-fusion-from-loading.html](http://www.ubuntumini.com/2008/11/stop-compiz-fusion-from-loading.html) - to stop compiz from loading, is this not enough to solve it as the problem is still occurring?

Not sure.  I have never had to edit gconf to stop Compiz in Ubuntu.

The easiest way is to just remove Compiz:
```
sudo apt-get remove compiz-core
```

---

### Post by AnRa on 2009-01-09
> **Mr. Mulder said:**
> i followed these instructions [http://www.ubuntumini.com/2008/11/stop-compiz-fusion-from-loading.html](http://www.ubuntumini.com/2008/11/stop-compiz-fusion-from-loading.html) - to stop compiz from loading, is this not enough to solve it as the problem is still occurring?[This](https://help.ubuntu.com/8.10/desktop-effects/C/compiz-configure.html) should be the best way.

---

