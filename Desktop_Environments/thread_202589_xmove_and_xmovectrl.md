---
title: "xmove and xmovectrl"
date: 2006-06-23
forum: Desktop Environments
---

### Post by domstyledesign on 2006-06-23
i have two video cards and two monitors.  i have a separate desktop on each and want to move application windows between them w/out using xinerama (it breaks some apps).

i found xmove in the repos but can't figure out how to use it.

the xmove server starts fine with just ```
xmove
```

but when i run ```
xmovectrl -list
```

i get ```
connect: Connection refused
```

however, even if i got something besides that, i'm not sure that i'd know what to do from there.  anyone have experience with this?

---

### Post by domstyledesign on 2006-06-26
*bump*

anyone?

---

### Post by luite on 2006-10-08
the xmove pseudo x-server listens on screen 1 by default. you have to instruct xmovectrl to talk to the xmove server and not the regular x server (on screen 0 probably).

something like:
```
xmovectrl :1 -list
```

I must admit I haven't yet managed to actually move windows, xmove and the x clients hang  when trying to move them:
```

luite@fritz:~$ xmove -server :0 &
luite@fritz:~$ Xnest :2 &
luite@fritz:~$ xeyes -display :1 &
luite@fritz:~$ xmovectrl :1 -move localhost -screen 2 1
```

I'll try to get that working at will let you know.

---

### Post by sehe on 2007-05-18
I have stumbled on all of these. Quick pointers here

Not authorized will be given when
1. the server does not respond (dead/not running)
2. the port is not bound (tcp listening off?)
3. no authentication (hehe). Use xauth or simply 
        DISPLAY=:1 xhost +
to temporarily allow all connections

Now, for the reason why you cannot get the move to actually happen: it is because you use an XNest for the sescondary X session. It results in an infinite loop. That's why you get no response. You'd probably percieve a quite high CPU usage as well.
      sudo killall xmove 
is your friend.

How to fix that? Try to use a proper X session instead of Xnest (X :2, e.g.) or look at Xvnc for a headless server. Xvnc is what i use. Then I use 1 XNest inside Xvnc to avoid having to 'enlist' every single client with xmove (by starting it on display :1). However *never* migrate any windows to the Xnest-ed server or you'll get bitten by the infinite loop again.

Also... once you kill xmove, the clients are inevitably stuck on their current server (in my experience). It might make more sense that the clients get killed with xmove but for some reason that doesn't happen. I guess the author of xmove played loose with proxying the X events here 

Regards
Seth

---

