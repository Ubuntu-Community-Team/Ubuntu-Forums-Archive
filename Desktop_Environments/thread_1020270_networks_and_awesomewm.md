---
title: "networks and awesomewm"
date: 2008-12-23
forum: Desktop Environments
---

### Post by fundae on 2008-12-23
Hi,

I'm an absolute beginner to using Awesome, so apologies if this is a stupid question.

When I login to awesome directly after booting up my computer - the network won't connect. If I login to GNOME and then log out and log in to awesome, the damn thing works. Any ideas on why this could be happening?

Is there a way to run the network manager applet in awesome?

Thanks in advance,
Pramod

---

### Post by Xiong Chiamiov on 2008-12-24
Is awesome at version 2 still in Ubuntu?  For me, in 3, the run dialog is win+f1, from which you can run 
```

nm-applet

```
Alternatively, if you want it to run automatically, edit your ~/.bash_profile and add
```

nm-applet &

```

---

