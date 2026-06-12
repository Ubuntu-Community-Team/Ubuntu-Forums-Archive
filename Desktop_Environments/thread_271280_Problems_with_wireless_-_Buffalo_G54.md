---
title: "Problems with wireless - Buffalo G54"
date: 2006-10-04
forum: Desktop Environments
---

### Post by kabads on 2006-10-04
I'm running the live disk to see what things are working before I
install. This is my first foray into wireless with Linux.

CD boots OK and runs. The Buffalo G54 network card is recognised as
eth0. However, when I go to System -> Admin -> Networking (using
Gnome) no network connection shows up to configure. I've tried sudo
ifup eth0 but get "Network unreachable".

Any advice on how to configure the WPA key and get it working? I've
read about ndiswrapper, but am not sure what it is or whether it
applies to my situation.

Adam

---

### Post by dyous87 on 2006-10-04
ok first do you see the network connection applet on your top pannel, if not right click on the panel and add it. Now click on that and make sure you type in eth0 under name. then click configure and you should see a wireless connection under the connections tab. click properties and just configure it with your ESSID and wep key. also make sure the enable this connection box is checked off. That should work....

---

### Post by kabads on 2006-10-04
I only see a network monitor, not a network connection manager when I try and add that applet.

---

### Post by dyous87 on 2006-10-04
> **kabads said:**
> I only see a network monitor, not a network connection manager when I try and add that applet.
yea that's the one sorry

---

