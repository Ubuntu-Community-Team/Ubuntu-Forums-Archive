---
title: "keyboard shortcuts not working"
date: 2013-02-13
forum: Desktop Environments
---

### Post by Kralizec on 2013-02-13
Hi all,

I haven't posted here in a while, mostly because my Ubuntu experience has been fairly smooth for a long time. I've just hit a problem that I haven't been able to resolve for myself, however.

I am running KDE4 as my desktop manager and none of my system keyboard shortcuts are working! That is, no alt+f2 for krunner, no alt+f1 for menu, not even alt+f4 for window closing (the most annoying).

I looked through my ~/.xsessionerrors and saw nothing untoward. I have tried logging out and logging back in (no effect) and I have tried restarting X (no effect). I have not yet tried restarting the computer.

With my research I came across several antiquated posts (2008-ish) that no longer seemed relevant. One solution I saw that I didn't try (because I don't want to rebuild my environment) was to delete my ~/.kde folder.

Any insight or advice would be appreciated. Thanks!

---

### Post by lordievader on 2013-02-14
A few things come to mind. Have you checked in the System Settings -> Shortcuts and Gestures if the keyboard shortcuts are enabled?

Have you upgraded to KDE 4.10? I've heard that for some people this breaks the screen lock keyboard shortcut.

A way to test if the error is due to a kde config file is to make a new user and test if this user has the same problem. If the new user does not, the problem is probably in some kde config file.

Hope this gives you a clue to solving the problem,
-lordievader.

P.s. there is bug 311050, partly describes the bug you are experiencing. Perhaps a good idea to take a look at it: [https://bugs.kde.org/show_bug.cgi?id=311050](https://bugs.kde.org/show_bug.cgi?id=311050)

---

### Post by Kralizec on 2013-02-14
Shortcuts are definitely enabled. A restart did fix the issue, so the next time it crops up I'll try making a new account to see if it persists cross-account.

Thanks for your response!

Ps: I actually have a kind of opposite problem from that bug. Ctrl + alt + L does successfully lock my screen but most other shortcuts do not work.

---

