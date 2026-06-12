---
title: "KDE4 momentary video garbage upon drawing new objects"
date: 2008-08-30
forum: Desktop Environments
---

### Post by Zorael on 2008-08-30
On every machine I install KDE4 I get this bug, and I'm not confused why I'm not seeing other people complaining about it.

[https://bugs.launchpad.net/ubuntu/+source/kubuntu-kde4-meta/+bug/254468](https://bugs.launchpad.net/ubuntu/+source/kubuntu-kde4-meta/+bug/254468)

[quote=me]Whenever a new object is drawn, such as the application menu or any application whatsoever, the space in which it will be drawn is first allocated with video garbage. After a brief delay - perhaps 200ms - the garbage is properly replaced with the real object contents. It looks as if it's displaying "old" video memory, if that makes sense. It is hard/impossible to get a proper screenshot depicting this.[/quote]

Is everyone else simply not experiencing this, or is there some really easy workaround I seem to have missed?

---

### Post by Zorael on 2008-11-29
Digging this up to raise awareness, since the behavior persists in Intrepid (4.1.3 from backports).

If you experience this as well, please consider confirming (and voting) for the bug over at [http://bugs.kde.org/show_bug.cgi?id=170462](http://bugs.kde.org/show_bug.cgi?id=170462), as well as at the previously linked launchpad entry. Developer attention is the first step.

---

### Post by benerivo on 2008-11-29
Yes this is an annoying. Graphics performance on kde4 in general (even on kde4.2 beta) is poor on my computer so i never realised that this was a bug until i read this thread. I hope it will be fixed for the final release of 4.2.

---

### Post by aos101 on 2008-11-30
Glad it's not just me finding this really annoying :)  I filed [a bug about this in plasma](http://bugs.kde.org/show_bug.cgi?id=164330) but Aaron thought it wasn't a plasma issue.  I usually only find it when right clicking on the desktop or bringing up the kicker menu.  I have found the issue exists on the Kubuntu 8.10 live CD, but strangely not at all with the Fedora 10 KDE live CD, so Fedora seems to be doing something different which avoids the issue.

---

