---
title: "ssh + vncviewer, faster using XP"
date: 2009-04-03
forum: General Help
---

### Post by whitethorn on 2009-04-03
I have a vnc connection setup, and I want to use a tunnel a port to my vncserver.  I open a terminal at my university and type

```
ssh user@*****.dyndns.org -p 43020 -L 4901:localhost:4900
```

I then open another terminal, and type

```
localhost::4901
``` 

It asks me for my password, and then it starts to try to remove my desktop background.  It takes about a minute for it to show the display. It's unusable really.

In XP when I use putty, with the same port forward, then vncviewer.  It usually takes about 1-2 seconds to refresh the screen.  Which is a lot faster. I have an upload of about 100kb/s, so it shouldn't be a network problem.  Any ideas?

---

