---
title: "Ubuntu 22.04 RPi 4: Krusader and Putty not working"
date: 2022-04-25
forum: Desktop Environments
---

### Post by patrick-jp on 2022-04-25
I installed Ubuntu 22.04 Desktop on my RPi 4 and then installed Krusader and Putty. Both state "connection refused" when I try to start a session connection. OpenSSH server is installed and running on all machines on the network, and both these applications worked on previous installs of 20.04. Has anyone else experienced this? and does anyone have a solution please? Note: CLI SSH commands work ... cannot understand why Krusader and Putty do not !?
Thanks for any help with this. Patrick.

---

### Post by TheFu on 2022-04-25
I'd check the version of ssh that putty uses.  Ensure it and the allowed encryption ciphers are compatible.  ssh has been dropping older, hackable, ssh ciphers in recent years.

For why Krusader doesn't work. I don't have a clue. Never touched it.
I'd use the equivalent of **ssh -vvvv** from each client to see what's happening during the working and non-working connections.

---

