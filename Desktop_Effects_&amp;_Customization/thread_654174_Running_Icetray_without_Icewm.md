---
title: "Running Icetray without Icewm"
date: 2007-12-30
forum: Desktop Effects &amp; Customization
---

### Post by PeterJS on 2007-12-30
I was browsing these fine forums the other day and came across a thread mentioning [lxp]("http://lxp.sourceforge.net/"), and decided to take a look at it for the novelty factor. With a bit of configuring it really does produce a desktop that looks like XP.

So I've got widgets and a task bar that look right but I'm hoping to run compiz with the monstrosity. I've been experimenting with it in a VM running hardy, yes I know compiz won't work in a VM so I've been using metacity to test with, when I run metacity --replace it kills icewm like it's supposed to, problem is that when icewm ends it takes the session with it dropping me back at gdm. In light of this I'm trying to work the other direction, running icewmtray from within the gnome desktop, and it's having none of it.
```

hardy-vm@hardy-vm:~$ lxp-icewmtray 
lxp-icewmtray: xinerama: heads=1
lxp-icewmtray: xinerama: 0 +0+0 800x600
lxp-icewmtray: using /home/hardy-vm/.lxp-icewm for private configuration files

```
That's the output I get in the terminal, but the taskbar never shows up.

Is it possible to run another WM in a session that started with IceWM? is it possible to run icewmtray without icewm?

---

