---
title: "Removing HAL but with networking working"
date: 2009-03-28
forum: General Help
---

### Post by Neo_The_User on 2009-03-28
When I turn off HAL In the boot script after running Xorg -configure, mouse, keyboard, and display work fine but for some reason, networking doesn't work. Is there a way manually load the network card from command line without HAL (Hardware abstraction Layer) as this is the only issue I'm having. I would basically like to have the network ethernet module for the VIA Rhine card loaded manually (or automatically without HAL or probing for other network devices)

---

### Post by Neo_The_User on 2009-03-28
bump

---

### Post by SuperSonic4 on 2009-03-28
Have you tried using the dbus deamon? I know hal depends on it but it could work on it's own like in arch

---

### Post by Neo_The_User on 2009-03-28
well in arch i dont have dbus or hal even installed and networking works.

---

### Post by SuperSonic4 on 2009-03-28
You could always try using a dhcpcd setup

---

### Post by Neo_The_User on 2009-03-28
My network doesn't support DHCP nor do I want it to as it is a security vulernability.

---

