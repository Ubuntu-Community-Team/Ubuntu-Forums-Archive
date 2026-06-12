---
title: "wireless switch"
date: 2009-09-05
forum: Dell Ubuntu Support (CLOSED)
---

### Post by threegremlins on 2009-09-05
Sometimes when I'm on the move and not using the wired network, I start up the system without turning on the wireless switch. When I turn it on after logging into to Ubuntu, Firefox or mail won't connect. Is there a command to activate the wireless, I know there must be one.

By the way, running Hardy LTS on a Vostro 1525, I've discovered when you install or re-install Hardy the first thing you must do before anything else is setup the wireless or you'll have nothing but problems trying to set it up later.

---

### Post by mikewhatever on 2009-09-05
Run ifconfig to find out your wireless interface name. It could be eth1 or wlan0, but lets assume it's eth1. Then **sudo ifconfig eth1 up**.

---

### Post by threegremlins on 2009-09-05
I knew it was as simple as that Thnx

---

