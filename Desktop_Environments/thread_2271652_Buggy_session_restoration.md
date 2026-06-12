---
title: "Buggy session restoration"
date: 2015-03-31
forum: Desktop Environments
---

### Post by pouleto3001 on 2015-03-31
Hi,
I've installed xubuntu 14.04 and when my previous session is restored after login (I've choosed "Automatically sauve session on logout" in Settings>Session and startup>General) pdfs that had been opened with evince or xpdf are empty windows that I find in my first workspace. Terminals or documents opened with geany are restored in their original workspace. On top of that, every few sessions my opened file manager windows may change of workspace or be closed... 
Something similar to [https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/1371144](https://bugs.launchpad.net/ubuntu/+source/xfce4-session/+bug/1371144) except that applications in the first workspace like evince are not properly restored, I was under xfce on debian wheezy, something old :p, and they were restored.
In the bug report above they say it's fixed in xfce 4.12, will it be in 4.10 or will Xubuntu 14.04 will upgrade to xfce 4.12? Has anyone experienced the same thing here?
Thanks.

---

### Post by pouleto3001 on 2015-04-02
Some precisions before I install kubuntu.
The installation was a Xubuntu 14.04.2 64 bits with all the last updates.
I've installed Okular and pdfs opened with it are properly restored. 
Evince and Xpdf don't show up in  Settings > Session and Startup > Session , Okular and FBReader do.
With settings > windows manager tweaks > focus > "when a  windows raises itself" : do nothing, evince pdfs are still closed but evince  windows won't change of workspace but FBReader will still move. Okular is all good.
Closed file manager windows occur after an error "thunar crashed with SIGSEGV in g_type_check_instance_cast()" after login in.

---

### Post by Toz on 2015-04-03
I reported the bug that you referenced in your first post. It was subsequently fixed in a recent commit (for GTK2 and some GTK3 apps). However, the issue is bigger than that bug report. I generally only use GTK2 apps (a couple of GTK3 and QT apps as well, but infrequently) thus I rarely run into the bug. However, I have noticed that the QT apps (e.g. Virtualbox) don't restore for me either.

Xfce session management is currently in a state of flux. See [this bug report]("https://bugzilla.xfce.org/show_bug.cgi?id=10963") for more information. It appears that GTK3 apps (using GTKApplication) and QT apps are not longer able to restore properly. The bug report talks about changes in the GTK3 infrastructure that led to this. It is something that the Xfce devs will be looking into - its on their TODO list.

---

