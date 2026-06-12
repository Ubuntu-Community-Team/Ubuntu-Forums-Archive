---
title: "tetrinetx - IPV6 only?"
date: 2009-03-20
forum: General Help
---

### Post by patryk77 on 2009-03-20
Hey,

I had a Tetrinet server running on my box for a while. Haven't played with it since I updated from Hardy to Intrepid.

Is it just me, or is tetrinetx currently only capable of running in IPV6 mode now?

```
netstat -a | grep 314
tcp6       0      0 [::]:31456              [::]:*                  LISTEN     
tcp6       0      0 [::]:31457              [::]:*                  LISTEN     
tcp6       0      0 [::]:31458              [::]:*                  LISTEN     

```

```
TetriNET for Linux V1.13.16+qirc-1.40c-IPv6
---------------------------------
Mar 20 23:06:44 Read game configuration from /etc/tetrinetx/game.conf
Mar 20 23:06:45 Listening at telnet port 31457, on socket 4, bound to 0.0.0.0
Mar 20 23:06:45 Listening at playback port 31458, on socket 5, bound to 0.0.0.0
Mar 20 23:06:45 Listening at query port 31456, on socket 6, bound to 0.0.0.0

```


I looked through the config files, but didn't find anything related...

Thanks


EDIT: Ok, I'm sure it IS IPV6 only. Question is how can I fix it ? :P

---

### Post by patryk77 on 2009-03-21
Wow, I am so dumb! ](*,)

Opened my ports in Webmin, but I didn't click on "Apply Configuration" :$

Does work now.

---

