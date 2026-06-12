---
title: "installed server kernel, now KDE unstable"
date: 2009-03-15
forum: Desktop Environments
---

### Post by tgilbert328 on 2009-03-15
Hi all,

I am running kubuntu 8.10 (kde 4.2 from unstable) (i386) and it has been rock solid, however I have noticed that between plasma and xorg and firefox that I usually had very little available ram even though I had 2gb.

So, with RAM so cheap, I went out and bought another 2gb bring it up to 4gb.  I noticed that the 32-bit kernel could only address ~3.2gb which led me to receive the advice to use the server kernel which includes PAE, allowing it to see 4gb.

I install and reboot and all is well.  However, after using KDE for a day or so, I have had several crashes, sometimes in klauncher, sometimes in plasma.  Prior to this change, i would characterize my system as stable.

My question is whether it is wise to use the linux-server kernel when I primarly use KDE/X Windows?

Result of uname -a:

```
Linux www.timgilbert.ca 2.6.27-13-server #1 SMP Thu Feb 26 08:12:00 UTC 2009 i686 GNU/Linux

```

Tim

---

