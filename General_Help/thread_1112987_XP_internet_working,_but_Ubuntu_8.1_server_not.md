---
title: "XP internet working, but Ubuntu 8.1 server not"
date: 2009-04-01
forum: General Help
---

### Post by ktamo on 2009-04-01
I've a problem. Recently I installed 8.1 Intrepid server on an old rig and I've been fiddling with it, installed a LAMP to it and followed ubuntugeek.com's 8.10 LAMP guide ([http://www.ubuntugeek.com/step-by-step-ubuntu-810-intrepid-ibex-lamp-server-setup.html](http://www.ubuntugeek.com/step-by-step-ubuntu-810-intrepid-ibex-lamp-server-setup.html)). I cannot ping any address besides localhost, and cannot install any packages. Before this I tried Ubuntu Desktop, and it couldn't connect either. I checked lpsci -a and it did recognise Realtek Semiconductor as ethernet device, so I doubt it's hardware related. 

On a second note, I have a WinXP installed on another hard drive on the same rig. With that internet works. 

I'm very new to networking and after spending the last day looking for reasons and possible fixes, I haven't found any working ones. The first problem occurred when I after editing /etc/network/interfaces/ I tried to "sudo /etc/init.d/networking restart", when it failed to bring up eth0. Also, during installation the DHCP auto-config failed and set it to configure it manually.

On my other PC I have Ubuntu 8.10 desktop, which connects to the internet perfectly (both of these PCs are connected to the same router, TW-EA200).

I'd appreciate any kind of help :???:

---

### Post by Sam Lars on 2009-04-03
You mentioned editing /etc/network/interfaces?  Could you post what is in that file now?

---

