---
title: "GTK apps and KDE"
date: 2008-04-04
forum: Desktop Effects &amp; Customization
---

### Post by Ahmed Shaheen on 2008-04-04
Hi ,
I'm using kubuntu 7.10, and I've installed a lot of gtk applications and gnome applications.
When I try to change the look and feel of these apps, it successes, but the font don't seem to be changed and viewed as I want.
I used  fedora before, the look and feel of gtk apps is not same as kubuntu.
How can I change it on kubuntu to give me the look and feel like the gtk apps look and feel on fedora.
Thanks a lot.

---

### Post by fela on 2008-04-04
i thought it's pretty hard to skin gnome apps well on KDE, and vice versa. If you use loads of gnome apps, why did you install kubuntu?

---

### Post by Ahmed Shaheen on 2008-04-04
Because I used it when I was new to Linux and I love it too.
When I used fedora I noticed that no differences between kde apps. and gtk apps. so I tried to make my kubuntu system like it.
can any one help me do that?

---

### Post by benerivo on 2008-04-05
There are some packages in the repositories, that can set your gtk theme to be similar to your kde/qt theme so that gtk apps fit in well with the kde environment. If you search for```
gtk qt engine
```in synaptic, you'll get a list of them you can use. Personally, i use kde4 with the gtk-qt-engine-kde4 package installed. This adds an additional option to the kde4 system settings, where you can set gtk apps to use your current kde4 theme. The end result is excellent, and all my gtk apps (exaile, vlc, etc.) look almost identical to my other native kde4 apps.

---

### Post by Ahmed Shaheen on 2008-04-06
Thanks benerivo,
But the problem not the engine, the problem in the font.
OK, no problem.
But now I have the same problem with kde4 I tried to search for the gtk-qt-engine-kde4 package you talked about but it seems that it was not in the repositories I use.
How can I install this package?

---

### Post by benerivo on 2008-04-06
I'm using kde4 from the ubuntu hardy repositories. Are you using kde4 from the gutsy (7.10) reps? It may be that the package i use is only available in hardy. In any case, check that you have enabled all extra repositories (main restricted universe multiverse). My /etc/apt/sources.list looks like this```
deb http://gb.archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse

deb http://gb.archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse

deb http://gb.archive.ubuntu.com/ubuntu/ hardy-proposed main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-proposed main restricted universe multiverse

deb http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu hardy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted universe multiverse
```
If you're using kde3, the version you want is just called gtk-qt-engine.

---

### Post by Ahmed Shaheen on 2008-04-06
I'm using ubuntu 7.10 .

---

### Post by benerivo on 2008-04-06
If your'e using kde4 from the gutsy reps, it may be that the gtk-qt-engine-kde4 package isn't available, and so you'll be unable to get gtk apps to look like apps in your kde4 desktop.

EDIT -  I don't think gtk-qt-engine-kde4 is in the gutsy reps. Only the gtk-qt-engine (the kde3 one) is available. See [here]("http://packages.ubuntu.com/gutsy/kde/").
EDIT #2 - Compare that with the hardy reps [here]("http://packages.ubuntu.com/hardy/kde/").

---

