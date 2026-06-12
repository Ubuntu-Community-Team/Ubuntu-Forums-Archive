---
title: "KDE 60% cpu with just file manager open"
date: 2009-09-02
forum: Desktop Environments
---

### Post by Ascenti0n on 2009-09-02
This post is just to share my 'concerned' experience.

I have been using KDE as my default session on Ubuntu 9.04, for about 3 weeks now.

Today I noticed that without any apps open and running, CPU usage runs at 20%. I noticed that with just Dolphin opened, that rate climbs to 80%, no other apps were running (foreground).

I tried different apps, one at a time and got the same results. Every time I open up just one app, the CPU usage climbs to 80% and stays there until that one app is closed.

I observed this with:
Dolphin, Konqueror (shares same libs), opening a terminal and running midnight commander, Kate.

I'm posting this as it may be of interest to somebody.

---

### Post by jacksaff on 2009-09-02
Do you have strigi (file indexing for desktop search) running?
I got strigi running a week ago and found that it made dolphin extremely slow, even when it was not actively indexing.

---

### Post by Ascenti0n on 2009-09-02
> **jacksaff said:**
> Do you have strigi (file indexing for desktop search) running?
I got strigi running a week ago and found that it made dolphin extremely slow, even when it was not actively indexing.

I havent used or started ANY desktop search index, at least not intentionally.

TBH, this is the first day I noticed such high CPU usage.

I even observed this over a ten minute period as I know when the system is working on any updates to download that takes up a lot of CPU, but that wasn't the case here.

---

### Post by krazyd on 2009-09-02
are you running nvidia proprietary driver?

run 'top' in a terminal. what's at the top?

---

### Post by Ascenti0n on 2009-09-02
I had to log back into KDE as I got fed up and logged into good'ol boring Gnome.

I ran 'top' which I had been running prior to logging out of KDE, and as I noted then, 'Kwin' is at the top.

2 points of note:

1. logging back into KDE, and with various apps open including Firefox 3.x and Dolphin, CPU usage rates are back to under 20%

2. When I logged into Gnome and started the system monitor, I noticed all was nice and low, with the same apps open as above.

---

### Post by krazyd on 2009-09-02
and are you using the nvidia driver?

---

### Post by Ascenti0n on 2009-09-02
YES, and I have the latest (Nvidia) driver installed (180.44)

---

### Post by krazyd on 2009-09-02
That's your problem. The nvidia drivers are known to be buggy, and unfortunately kwin uses some acceleration features which trigger those bugs. You could try upgrading to a newer nvidia driver from their website. Also ask around on nvnews.net forums - I've seen a few people with similar issues. Unfortunately, because the drivers are proprietary there's not much anyone except nvidia can do.
See here:
[https://bugs.launchpad.net/ubuntu/+source/kdebase-kde4/+bug/253279](https://bugs.launchpad.net/ubuntu/+source/kdebase-kde4/+bug/253279)
[http://linux.derkeiler.com/Mailing-Lists/Fedora/2008-07/msg01752.html](http://linux.derkeiler.com/Mailing-Lists/Fedora/2008-07/msg01752.html)

---

### Post by Ascenti0n on 2009-09-02
Thanks Krazyd for your time and insight.

---

