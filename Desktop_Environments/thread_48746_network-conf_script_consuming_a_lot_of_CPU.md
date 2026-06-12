---
title: "network-conf script consuming a lot of CPU"
date: 2005-07-13
forum: Desktop Environments
---

### Post by Sandu on 2005-07-13
System monitor displayed that every 2-3 seconds CPU usage jumps from 1-3 % to 15-20 %. It was script /usr/share/setup-tool-backends/scripts/network-conf. What does this script mean? How to disable this script?

---

### Post by Chrissss on 2005-10-26
Got the same problem here, too. I don't know what calls this script. Killing that perl process doesnt't help, cause after a couple of minutes the perl task is back...

Any ideas?

Thanks
 Christoph

PS: Perhaps some encounters the same problem. It was the gnome-modem-applet. YJust kick it out panel and everything is fine. You can check this by entering

# ps aux --forest

into a terminal. You can see now which application depends on which.

---

### Post by Dragonbite on 2006-03-21
I currently have a couple of those perl threads running, taking up CPU and I am able to stop them easily enough but they come back on reboot.

It would make sense that it is the gnome-modem-applet because I've had problem with them as is!

One problem is that I go through the motions to add it to the panel, and they never appear!  I wondered if they were running in the background or something.

So I'll have to try and delete those from the paneles and see if that fixes things but then I have a related question: what do I use instead if the gnome-modem-applet is causing such difficulties?

Right now I have to go into network-admin, select the modem and "activate" to get online.  I was hoping to use the modem-applet to make it easier.

---

### Post by grota on 2006-10-27
is the modem applet ... for this perl script glxgear and other glx application go slowly every 5-10 sec ... they have become crazy for this ! whith nvidia driver ...

---

