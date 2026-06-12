---
title: "xchat use port 80 possible?"
date: 2006-01-13
forum: General Help
---

### Post by towsonu2003 on 2006-01-13
I'm on dial up and my ISP (university) blocks almost all ports (includes 6667)... Is it possible to tweak xchat (or any other irc chat program) so that it uses port 80 instead of current port configuration? 

PS. currenly using cgi:irc for chat, not enjoying it ;)

PS2. server I want is freenode...

---

### Post by Randomskk on 2006-01-13
Basically; no - the freenode server will only accept connections on port 6667. However, if you have a machine OUTSIDE the uni network, you can encapsulate the IRC inside HTTP to that machine.
Basically, you have an IRC proxy (or a SOCKS / whatever type you want) proxy on the outside machine, and connect to that, and that forwards your request to where you want it.
IRC would work, as it doesn't matter so much with a few seconds of lag, but it's worth noting that for multiplayer games you're gonna get some slow speeds using a proxy like that.

---

