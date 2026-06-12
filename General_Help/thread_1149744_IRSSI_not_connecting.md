---
title: "IRSSI not connecting??"
date: 2009-05-05
forum: General Help
---

### Post by abhilashm86 on 2009-05-05
i'm not able to connect to IRC server, what is this error actually?
i give as /connect irc.freenode.net


22:26 -!- Irssi: Looking up irc.freenode.net
22:26 -!- Irssi: Unable to connect server irc.freenode.net port 6667 [Name or service not known]

---

### Post by Dr Small on 2009-05-05
See if it's a problem with IRSSI or DNS:
```
telnet irc.freenode.net 6667
```

---

### Post by abhilashm86 on 2009-05-05
> **Dr Small said:**
> See if it's a problem with IRSSI or DNS:
```
telnet irc.freenode.net 6667
```

its with irssi i guess, a remote server freenode is not able to connect,
```
abhilash@abhilash-desktop:~$ telnet irc.freenode.net 6667
telnet: could not resolve irc.freenode.net/6667: Name or service not known

```

---

### Post by andrew.46 on 2009-05-28
Hi abhilashm86,

Did you manage to resolve this issue?

Andrew

---

