---
title: "xdmcp with firehol"
date: 2008-05-17
forum: Desktop Environments
---

### Post by jpfink on 2008-05-17
I am trying to use xdmcp on 8.04. I use firehol and have opened the xdmcp service. I was able to create a session with the remote machine but only got a black screen with a "X". I then opened tcp/udp ports 6000-6063 for x11 and got a tan background with a white box in the top left of the screen. It seems as if there are more ports that need to be opened up.

XDMCP works wonderfully when I drop the firewall.

Any ideas?

Later, I noticed in a post that disabling ESD in the Sound Preferences would resolve this. I tried it and it works! I don't know how they are related.

---

