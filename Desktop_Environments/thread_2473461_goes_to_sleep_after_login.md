---
title: "goes to sleep after login"
date: 2022-04-05
forum: Desktop Environments
---

### Post by Jaxilian on 2022-04-05
Hi

I have a problem which occurs on both Dell and HP laptops when docked (both the usc-c dock WD19TBS for Dell and the mechanical slim dock för HP). When I login when being connected to the docks, it takes about 5 -10 sec then laptop goes down to sleep and screen goes black. I press space bar and it takes same time and it comes back with screen again.
I use Ubuntu 20.04.4

I have tried modifying the line HandleLidSwitchDocked=ignore (removing the #) in the file /etc/systemd/logind.conf
It has no effect whatsoever.

Anyone know why this happens?

---

