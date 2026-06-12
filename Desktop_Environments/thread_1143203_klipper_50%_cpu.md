---
title: "klipper 50% cpu"
date: 2009-04-29
forum: Desktop Environments
---

### Post by rcmn on 2009-04-29
since i upgade to 9.04 klipper show 50% cpu utilisation and I can't manage to make it appear in the systray.
Does anyone else have issue with klipper?

---

### Post by Zorael on 2009-04-29
I had it during the Jaunty beta and couldn't fix it, so I can sort of confirm it as a bug. If you kill klipper and then start it from a command line, it'll spout an error message that you need to start some helper app first, if memory serves. Then it soars in cpu usage.

If you want to completely stop it from being autostarted, I think you need to remove the klipper.desktop file somewhere in **/usr/share/autostart/kde4/**, or thereabouts.

You may also want to stop by launchpad and post a bug report about it; developers can't fix bugs they don't know of.

---

### Post by rcmn on 2009-04-30
I did notice the error message when starting Klipper from the console. I was planning on stopping by launchpad eventually , but I wanted to gather more info first and make sure there is not an easy fix .
As far as /usr/share/autostart/kde4/ I'll look into it tonight.
Thx.

---

