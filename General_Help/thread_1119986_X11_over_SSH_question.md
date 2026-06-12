---
title: "X11 over SSH question"
date: 2009-04-08
forum: General Help
---

### Post by Tralce on 2009-04-08
So I doubt it's entirely possible, but I was wondering.

Is there a way to change the display that a *running* program uses? For example, say I SSHed into my Ubuntu machine on which Transmission is always running, I'd like to have a command that redirects the default x11 display output to the screen that SSH runs. That way, I could remotely interact with the program using SSH's display number 10, then once done, redirect it back to display 0.

Is this even possible?

---

### Post by whoop on 2009-04-08
ssh supports X protocol forwarding. If you have a graphical application on the ssh server and you have the same graphical application (same version also) on the client you can make use of this technology.
```

ssh -X username@server

```

you can also start a program directly:
```

ssh -X username@server 'application'

```

---

### Post by The Cog on 2009-04-08
There is no way to do that that I am aware of. When I want to do something like that, I use a console program called **screen** that allows me to disconnect (maintaining a virtual screen for hte program to continue writing to), then reconnect later and re-attach to the virtual screen. Then I use the console version of transmission.

---

