---
title: "SSH port forwarding/tunneling?"
date: 2006-03-21
forum: Desktop Environments
---

### Post by Coutsos on 2006-03-21
I've read about this many times before but I can't seem to understand it, or at least, I can't get it to work for my particular situation.

Say I'm on my laptop and want to connect to IRC, but the network I'm on blocks port 6667. I have shell access on a server that allows access to that port, and I could just SSH to it and run irssi or some other text IRC client, but sometimes I'd just rather use X-Chat. Isn't it possible to use SSH to get any traffic my laptop tries to send on a specified port and instead send it on the port on the server?

The command seems to be:
ssh remotehost localport:remotehost:remoteport

But that doesn't work. Am I doing something wrong here? (and would this post be better suited for another forum section?)

Thanks in advance

---

