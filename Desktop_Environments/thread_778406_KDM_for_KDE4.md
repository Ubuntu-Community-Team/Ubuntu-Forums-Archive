---
title: "KDM for KDE4"
date: 2008-05-02
forum: Desktop Environments
---

### Post by yodermk on 2008-05-02
Hi,

Recently upgraded to Hardy by network.  Installed kubuntu-kde4-desktop.

It had been using the KDM from KDE3 and I was able to boot into KDE4.  (I literally can't use KDE3 because every time I boot into it it makes a horrible loud whining noise.)  But whenever I exit, it goes back to the hardware text mode.  KDM does not restart.  Also, when I click the Switch User feature in KDE4, it just brings up the Run Application dialog as though I pressed Alt-F2!

I'm trying to convert to KDM in KDE4 hoping that will fix the issues.  But, even when I set /etc/X11/default-display-manager to /usr/bin/kdm-kde4, when I try to start kdm-kde4 I get:

```
Not starting K Display Manager (kdm-kde4); it is not the default display manager.
```

Hopefully I can find something workable.  I really need the Switch User feature, which worked fine in Feisty and Gutsy.

Thanks!

---

### Post by Xiong Chiamiov on 2008-05-02
What about when you run
```

sudo dpkg-reconfigure kdm4

```

---

### Post by yodermk on 2008-05-02
> **Xiong Chiamiov said:**
> What about when you run
```

sudo dpkg-reconfigure kdm4

```

You mean "kdm" or "kdm-kde4"?  Tries both of those, selected KDM and KDM4 from the menu, and no change.  Should probably file it in Launchpad.

---

