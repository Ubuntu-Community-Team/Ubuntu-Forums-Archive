---
title: "qt designer and window decoration problem"
date: 2009-05-18
forum: Desktop Environments
---

### Post by ebutz on 2009-05-18
Dear all, 

I have kubuntu 8.10 running on an IBM thinkpad. I have the following problem:

Running the qt designer via ssh -X, the window decorations do not show, and the window is fixed to the upper left part of the screen. This only happens for the remote window, I can run the designer locally without problems, not even any warning is shown in the parent terminal window. 

The problem is not related to the remote system either, since I have it also on a different remote system and cannot reproduce the problem when starting the designer from another machine. 

Any hint on how this comes about and what can be done about it would be gladly appreciated. 

Cheers, 

Erik

---

### Post by ebutz on 2009-05-19
I should add that this happens _only_ with the qt designer (at least I haven't found another application which causes the same trouble). The window decorations work fine, both locally and remote for other applications (like emacs or gedit). 

Cheers, 

Erik

---

### Post by krazyd on 2009-05-19
> **ebutz said:**
>  cannot reproduce the problem when starting the designer from another machine. what's the other machine running?

---

### Post by ebutz on 2009-05-19
Hi krazyd, 

the other machines are running scientific linux 4 with some kde 3.x or gnome. 

Cheers, 

Erik

---

### Post by krazyd on 2009-05-21
That's strange. sorry, I'm not sure what the issue is - x forwarding works for me here on Kubuntu 9.04, but I don't have qt designer installed on the remote machine. 

qtconfig works.. :?:

---

### Post by ebutz on 2009-05-25
I also don't have any idea what the problem is. 

If I run ssh in verbose mode, I get the following output both for a working X forwarding (ie. with window decorations) and the designer which does not have the decorations:

```

debug1: client_input_channel_open: ctype x11 rchan 3 win 2097152 max 16384
debug1: client_request_x11: request from 127.0.0.1 37640
debug1: channel 1: new [x11]
debug1: confirm x11
debug1: channel 1: FORCE input drain

```

so also there, not hint on any problem. 

Is there any other debug prints I could look at?

Cheers, 

Erik

---

### Post by krazyd on 2009-05-25
maybe you could try asking on IRC. #kde or #kubuntu ?

---

### Post by ebutz on 2009-05-27
Hi, 

I can now narrow this down to probably a problem with kwin, since I can start metacity (on the remote machine) and this will solve the problem even though this is of course not really a real solution.

---

### Post by ebutz on 2009-06-10
Another piece of information: 

The problem persists under kubuntu 9.04 and is clearly related to kwin.

When I do a ```
kwin --replace
``` to get the output to a terminal, I get:

```
kwin: X Error (error: BadPixmap [4], request: X_FreePixmap[54], resource: 0x143f836)
```

when starting a designer on the remote machine copiously (dozens if not hundreds of messages). 

Cheers,

---

