---
title: "Ubuntu Reload Kills Network Connection"
date: 2005-10-10
forum: Desktop Environments
---

### Post by capi on 2005-10-10
I'm having troubles with my network staying up. Specifically I've tried 
two different cards and switching out the cables. I'm on a dual-boot 
Kubuntu/WinXP. However the same thing happened when it was Ubuntu/WinXP.

When it goes out both Windows and Ubuntu loose connection, however 
everything else on the (Linskys)router works fine. It's only happened in 
the boots I've done in the past weeks. Everything works fine until 
around the third reboot of Ubuntu when the network dies.(there's 
probably a beter term since it's not the network, just the one computers 
ability to connect to the network). 

The only thing that has worked thus far is to reinstall Ubuntu. Thats 
obviously not a good solution. I've tried messing with 
/etc/network/interfaces to change back and forth between dynamic and 
static address'. 

ifconfig either gives me a ipv6 address or 127.0.0.1(localhost does 
still work).

Any guesses, it doesn't seem to be hardware related and my guess is that 
Ubuntu is either messing with the router and blocking the computer from 
grabbing an IP at boot, or corrupting something. I'm really out of ideas 
myself.

[i]Please excuse any ugliness that may come with this post. I'm doing 
this 
through w3m and I don't know how it will look.[/i]

most grateful,
~capiCrimm

---

### Post by mlomker on 2005-10-10
> ifconfig either gives me a ipv6 address or 127.0.0.1(localhost does 
still work).

You are using wired ethernet and eth0 disappears or are you using wireless?

There are some diagnostic commands that could be tried when it occurs.  The first thing to confirm would be that the drivers are loading.

This at a prompt would be a place to start:

```

dmesg | grep eth

```

---

