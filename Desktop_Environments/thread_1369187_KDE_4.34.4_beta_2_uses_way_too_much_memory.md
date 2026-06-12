---
title: "KDE 4.3/4.4 beta 2 uses way too much memory"
date: 2009-12-31
forum: Desktop Environments
---

### Post by ElTimo on 2009-12-31
Having installed Kubuntu Karmic on top of an existing Gnome install, I noticed that KSysGuard in KDE 4.3 reports ~600 MB being used *while idle.* Compare this to Gnome, which idled normally around 200-300 MB. Thinking there might be a bugfix for this with 4.4, I upgraded to the beta, but if anything the problem got worse. The odd part is that, when adding up the amounts of memory used by individual applications, the total comes out to about 450 MB, which seems far more reasonable. My question now is this: what the $(^*%& is going on? Gnome never had this problem, but I'm not really a fan of Gnome anymore.

---

### Post by schnelle on 2010-01-01
I am using Kubuntu 9.10, KDE 4.3.4. When system boots up with amarok, kmess and skype it consumes about 350mb. Without these programs it takes about 230mb.

---

### Post by SuperSonic4 on 2010-01-01
I'm using 970mb KDE 4.4 beta 2 although I am compiling and running ff and amarok.

Frankly I don't see what the fuss is about, I might be using about 1GiB but I still have 7GiB free..

Is there even a problem with using the ram?

---

### Post by jrusso2 on 2010-01-01
What was the old saying?  Unused ram is wasted ram?  Something like that.

---

### Post by 3Miro on 2010-01-01
Which apps are you using. A single GTK app (such as Firefox or Transmission or gedit or Totem) you boost the memory usage tremendously (since it has to load the GTK libraries in addition to the QT ones). Also do you have Kwin effects enabled, Gnome + Compiz takes over 500MB for me.

---

### Post by 3Miro on 2010-01-01
> **jrusso2 said:**
> What was the old saying?  Unused ram is wasted ram?  Something like that.

Linux never wasted RAM, it caches the hard-drive in it. KDE has an applet that shows RAM usage + Swap + Cashed HD.

---

### Post by VMC on 2010-01-02
I'm not sure I fully understand how the ram is used. I just realized, using 'top', that even in Ubuntu, there is reported almost all of my ram in use. Then I just tried using one of the ram monitoring apps, and it reports only 350meg of ram usage?!

---

### Post by GeneralZod on 2010-01-02
> **VMC said:**
> I'm not sure I fully understand how the ram is used. I just realized, using 'top', that even in Ubuntu, there is reported almost all of my ram in use. Then I just tried using one of the ram monitoring apps, and it reports only 350meg of ram usage?!

Lots of details here:

[http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html](http://forums.gentoo.org/viewtopic-t-175419-postdays-0-postorder-asc-start-0.html)

In a nutshell: some RAM monitors will include cached files; others don't.

---

### Post by trumpeteersman on 2010-02-12
I have the same issue.  Karmic 2.6.31-17-generic x64.
4:4.3.5-0ubuntu1~karmic1
1GB of memory.

With all effects turned off and 2 tabs from Firefox just after bootup takes 51% of my 1GB.  When I use more than 80%, it begins swapping even with a swappiness of 0.

Every once in a while I boot up to 25% which is great, but this occurs infrequently.

Even worse, another issue plagues me:  When the HDD is under stress, the UI becomes unresponsive(even ctrl-alt-F1).  So when I start swapping at 80% capacity,  I have to wait 1-2 minutes to be able to do anything.

This is the second system with kde4(out of 2) with this problem.  I do not think this is merely a "how apps see cache in memory" issue.

---

