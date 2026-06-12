---
title: "kbuildsycoca4 crashing with SIGABRT in KDE 4.0.2"
date: 2008-03-10
forum: Desktop Environments
---

### Post by StarsAndBars14 on 2008-03-10
Ok so the problem is ... when I try to log in to the new version of KDE (on Gutsy) I end up sitting at the part of the KDE 4 splash screen where the white disk is flashing for 20 seconds, and then I get SIGABRT crashes in kbuildsycoca4.  The backtrace box keeps coming up after I close it with the same error and I can't save a log - also for that reason.  But I did manage to get a pad of paper and a pen to write down the main part of the backtrace:

```

Thread 1 (Thread -1232202048 (LWP 10629)):
#0: 0xffffe410 in __kernel_vsyscall()
#1: 0xb7de8e70 in nanosleep() from /lib/tls/i686/cmov/libc.so.6
#2: 0xb7de8ca7 in sleep() from /lib/tls/i686/cmov/libc.so.6
#3: 0xb7900640 in ?? () from /usr/lib/kde4/lib/libkdeui.so.5
#4: 0x00000001 in ?? ()
#5: 0x00000000 in ?? ()
#0: 0xffffe410 in __kernel_vsyscall()

```

I've already looked on the bug trackers for both KDE and Ubuntu, neither one show up.

If this can be chalked up to a mis-installation, I'll be more than happy to reinstall KDE4 but I want to get some opinions first.  Thanks!

---

### Post by firephoto on 2008-03-10
Try deleting the plasmarc and plasma-appletsrc files.

rm ~/.kde4/share/config/plasma*

Someone had the same issue last night on irc and that seemed to fix it. Your error is identical and it was plasma crashing for them due to a bad config caused by something. They actually removed ~/.kde4 but it's most likely just the plasma configs but you can clean it all up if needed.

---

### Post by rax_m on 2008-03-10
Unfortunately I'm having the same issue and deleting .kde4 directory doesn't solve it. 

This is my first install of KDE4 so wouldn't have thought any old settings would cause an issue. 

Basically during the splash loader you get a load of errors thereafter I get a black screen with my mouse cursor (which works). Thereafter nothing happens (even after 5 minutes).

---

### Post by dandelo on 2008-03-10
I have the same problem in ubuntu gutsy with kde 4.0.2!
But with the mouse I see also the Avant Window Navigator!!?? But I use it in gnome with compiz, not in kde4!

With kde 4.0.1 this bug there wasn't.

How to solve?

Thank you

---

### Post by StarsAndBars14 on 2008-03-10
> **rax_m said:**
> Unfortunately I'm having the same issue and deleting .kde4 directory doesn't solve it. 


Yeah I tried that before starting this thread here too and it didn't work.

---

### Post by MarcosSoares on 2008-03-11
[https://bugs.launchpad.net/ubuntu/+source/kde4libs/+bug/199145](https://bugs.launchpad.net/ubuntu/+source/kde4libs/+bug/199145)

In resum, my problem has solved removing switchfox.

---

