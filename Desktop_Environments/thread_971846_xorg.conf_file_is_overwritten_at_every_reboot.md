---
title: "xorg.conf file is overwritten at every reboot"
date: 2008-11-05
forum: Desktop Environments
---

### Post by pico on 2008-11-05
Hi!

I want to set the desktop resolution on my Ubuntu 8.04
Of course I can set it manually Using the GUI, but after reboot this changes are lost and there is no checkbox to "set default setting".

So I have edit the /etc/xorg.conf but even in this case, after reboot this file is overwritten and my setting are lost!

So..
How I can set my desktop resolution ?

Regards

PiCo

---

### Post by kellemes on 2008-11-05
You have some display-manager running that edit's your configuration files at every boot? It sounds like it..

---

### Post by pico on 2008-11-05
how can I investigate what you say?

---

### Post by Coreigh on 2008-11-05
I think xorg does a dynamic config on every startup. HOWEVER ...

When I go to System >> Preferences >> Screen Resolution and set the setting of my choice it stays. There is also a checkbox that says "Make default for this computer..." You do not have this?

I am on Gutsy (7.10)

---

### Post by pico on 2008-11-05
No.
Unfortunately I haven't this check box (I'm on Ubuntu 8.04). And my setting are loose at reboot....


Any suggestion ?

---

