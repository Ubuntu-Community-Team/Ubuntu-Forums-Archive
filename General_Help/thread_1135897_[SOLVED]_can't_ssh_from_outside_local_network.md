---
title: "[SOLVED] can't ssh from outside local network"
date: 2009-04-24
forum: General Help
---

### Post by cyran on 2009-04-24
Heh. Never mind, ignore me. After a week of being puzzled, solved it myself immediately after posting.

[SIZE="1"]This is weird, because it was working before, and I'm not sure what I changed.

I have my router set to forward port 22, port 80, and some other ports to my Xubuntu 8.10 desktop (with a static IP). I could SSH to it on port 22 just fine before, both from a laptop on the local network and from somewhere else. But now when I try SSH'ing "from outside," it only says "ssh: connect to host [foo] port 22: Connection refused". Local SSH connections to the static IP still work. [The open ports test site]("http://www.yougetsignal.com/tools/open-ports/") still says port 22 is open.

I'm using a cryptographic key to login, with passwords disabled, but that was all working just fine before.[/SIZE]

---

