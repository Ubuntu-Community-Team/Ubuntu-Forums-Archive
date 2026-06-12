---
title: "krusader fails to start"
date: 2009-06-12
forum: Desktop Environments
---

### Post by max7 on 2009-06-12
krusader is #1 program. It is very best software and stopped to work :(

I get error when I am starting krusader

A Fatal Error Occurred

The application Krusader (krusader) crashed and caused the signal 11 (SIGSEGV).
Please help us improve the software you use by filing a report at [http://bugs.kde.org](http://bugs.kde.org). Useful details include how to reproduce the error, documents that were loaded, etc.

Application: Krusader (krusader), signal SIGSEGV
0x00007f0a130f3cf0 in nanosleep () from /lib/libc.so.6

Thread 1 (Thread 0x7f0a18033750 (LWP 4594)):
[KCrash Handler]
#5  0x0000000000453dea in _start ()

----

I thought it relates to updates and I rebooted machine. Same problem.
I have to learn dolphin now that I very dislike :(

Please, help!

---

### Post by aged hippy on 2009-06-12
It may be worth trying a *remove* and *purge* then re-install it.

Or try Konqueror....

---

### Post by max7 on 2009-06-12
Thank for your response. I just have 

mv .kde/share/config/krusaderrc .kde/share/config/krusaderrc2

And it started to work

---

### Post by aged hippy on 2009-06-13
> **max7 said:**
> Thank for your response. I just have 

mv .kde/share/config/krusaderrc .kde/share/config/krusaderrc2

And it started to work

:D Nice one.

---

### Post by karlooo on 2009-07-17
hi, it seems that i have the same problem. krusader simply crashes directly after starting. removing personal configuration files (.kde/share/apps/krusader) does not help. completely removing and re-installing (including purging all configuration files) krusader does also not help.

just installed debug symbols and produced this nice error message:

 p, li { white-space: pre-wrap; }  Application: Krusader (krusader), signal SIGSEGV
 
 > Thread 1 (Thread 0xb5331700 (LWP 2023)):
 [KCrash Handler]
 #6  0x0808aaf8 in PanelManager::slotChangePanel (this=0x9abb8e0, p=0x0) at /build/buildd/krusader-2.0.0/krusader/panelmanager.cpp:71
 #7  0x08095f26 in KrusaderView::start (this=0x9935580, leftTabs=
           {<QList<QString>> = {{p = {static shared_null = {ref = {_q_value = 10900}, alloc = 0, begin = 0, end = 0, sharable = 1, array = {0x0}}, d = 0xbfab491c}, d = 0xbfab491c}}, <No data fields>}, leftTypes={{p = {static shared_null = {ref = {_q_value = 10900}, alloc = 0, begin = 0, end = 0, sharable = 1, array = {0x0}}, d = 0xbfab4920}, d = 0xbfab4920}}, leftProps=
         {{p = {static shared_null = {ref = {_q_value = 10900}, alloc = 0, begin = 0, end = 0, sharable = 1, array = {0x0}}, d = 0xbfab4924}, d = 0xbfab4924}}, leftActiveTab=0, rightTabs=
           {<QList<QString>> = {{p = {static shared_null = {ref = {_q_value = 10900}, alloc = 0, begin = 0, end = 0, sharable = 1, array = {0x0}}, d = 0xbfab4928}, d = 0xbfab4928}}, <No data fields>}, rightTypes={{p = {static shared_null = {ref = {_q_value = 10900}, alloc = 0, begin = 0, end = 0, sharable = 1, array = {0x0}}, d = 0xbfab492c}, d = 0xbfab492c}}, rightProps=
         {{p = {static shared_null = {ref = {_q_value = 10900}, alloc = 0, begin = 0, end = 0, sharable = 1, array = {0x0}}, d = 0xbfab4930}, d = 0xbfab4930}}, rightActiveTab=1, leftSideActive=false)
     at /build/buildd/krusader-2.0.0/krusader/krusaderview.cpp:142
 #8  0x080a6514 in Krusader (this=0xbfab4ab4) at /build/buildd/krusader-2.0.0/krusader/krusader.cpp:376
 #9  0x08092d9a in main (argc=3, argv=0xbfab4a70) at /build/buildd/krusader-2.0.0/krusader/main.cpp:240
 
 

actually i was expecting a little bit more information. i'm also not really williing to dig deep into krusader's code...
does anyone have an idea how to fix this issue, or what might cause this problem?
it's a  jaunty system, krusader --version gives:
Qt: 4.5.0
KDE: 4.2.2 (KDE 4.2.2)
Krusader: 2.0.0 "Mars Pathfinder"

---

### Post by GeneralZod on 2009-07-17
> **karlooo said:**
> 
does anyone have an idea how to fix this issue, or what might cause this problem?


File a bug report at bugs.kde.org - krusader is registered there.

---

### Post by karlooo on 2009-07-18
"solved". it seems that the immediate crash was caused by some common/global kde configurations. completely removing .kde (after backup) including kdeglobals and starting krusader without a valid configuration did not result in a segmentation fault.
diff and merging of old configuration files and newly created files did, however, does not really give hints on what went wrong. with my original krusaderrc krusader also starts, so in principal it has to be something in kdeglobals. i was, however, not able to reproduce the immediate crash after startup. 
so for me it's solved, just delete all krusader-relevant files, restart, et voila!
i did not file a bug report since there are already several related but unconfirmed reports on bugs.kde.org. unfortunately, i also do not remember what packages i have installed/uninstalled causing the problem.

---

