---
title: "Background applications in GNOME"
date: 2010-05-26
forum: Desktop Environments
---

### Post by bunburya on 2010-05-26
Hi all, I'm just moving to GNOME from KDE so there are a few things that I'm not quite used to.

One such thing is the behaviour of certain programs in the background once you close their windows. For example, in KDE, once you closed Akregator's window the program itself would keep running, visible (and accessible) in the bottom-left corner of the screen. While in this state it would still search for and fetch updates for your blog feeds. I think KMail was the same though I never really used it.

This doesn't seem to happen in GNOME. With both Evolution and RSSOwl, closing the program's window via the "X" button at the top seems to completely end the operation of the program; no more fetching mail or blog updates. You have to start the program up fresh if you want that.

Am I correct that this is happening? If it is, is there any way to change it?

---

### Post by isaacj87 on 2010-05-26
I believe Evolution is still running. If you're on Ubuntu 10.04, Canonical implemented an indicator applet that houses your chat, email and social clients. You'll see a little envelope icon towards the top right. After opening Evolution, you'll be able to access it more easily from this area.

One way to make sure, open up the system monitor (System -> Administration -> System Monitor) and see if an Evolution process is still running.

---

### Post by bunburya on 2010-05-26
Thanks for the tip. I checked and it does indeed say that evolution-notify-alarm and evolution-data-server-2.28 are running (sleeping). I presume this means that Evolution is doing its thing in the background.

RSSOwl is not listed though. I take it this is just a result of RSSOwl not being native GNOME software. A shame but not the end of the world.

---

### Post by Barafu Albino Cheetah on 2010-05-26
Use Liferea for RSS in Ubuntu.

---

