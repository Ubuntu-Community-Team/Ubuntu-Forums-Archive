---
title: "Beryl causes networking issues?!?!?!"
date: 2007-01-09
forum: Desktop Environments
---

### Post by gp2x on 2007-01-09
Weirdest issue ever....

Im running XGL/Beryl on Ubuntu EE, which is nice. However, when I perform something network intensive (eg, installing something) the network card in my laptop (Broadcom Corporation BCM4401-B0 100Base-TX) stutters a bit, loses its IP, the regains it again (before losing it again).

ie.
Jan  9 13:49:33 beast dhcdbd: message_handler: message handler not found under /
com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Jan  9 13:49:33 beast dhcdbd: message_handler: message handler not found under /
com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Jan  9 13:49:33 beast dhcdbd: message_handler: message handler not found under /
com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Jan  9 13:49:33 beast kernel: [17192425.808000] rtc: lost some interrupts at 204
8Hz.
Jan  9 13:49:33 beast kernel: [17192425.924000] rtc: lost some interrupts at 204
8Hz.
Jan  9 13:49:33 beast kernel: [17192426.032000] rtc: lost some interrupts at 204
8Hz.
Jan  9 13:49:43 beast kernel: [17192436.608000] b44: eth0: Link is down.
Jan  9 13:49:45 beast kernel: [17192438.608000] b44: eth0: Link is up at 100 Mbp
s, full duplex.
Jan  9 13:49:45 beast kernel: [17192438.608000] b44: eth0: Flow control is off f
or TX and off for RX.

Im not sure if the lost interrupts or missing message handlers are significant.

Thing is, if I change WMs to metacity this problem clears up!

Any clues? Where can I start to troubleshoot this?

Thanks

---

### Post by gp2x on 2007-01-11
Further to this:

This definitely has something to do with beryl - if I reload the window manager the problem disappears (for a while). Another symptom of the problem is that audio stutters....

IRQ problem? I dont get it. Beryl doesnt crash/misbehave, it just affects other programs including a kernel module?

---

