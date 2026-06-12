---
title: "Lost internet &amp; network connection Ubuntu 9.04"
date: 2009-06-24
forum: General Help
---

### Post by csolomon on 2009-06-24
I can no longer connect to the internet or print through the network; the problem is ONLY on my Ubuntu 9.04 machine.

My other computers are connecting to the internet (DSL) with wireless, and my Ubuntu machine is connecting to the wireless, but it can't get on the internet with either wirless or with ethernet.  (It is on a Lenovo R61e).   Everything worked with Ubuntu 8.04 and everything worked after I upgraded to Ubuntu 9.04 two days ago, until I shut down last night.  I booted today and the only connection that works is a USB printer connection; I cannot get to the network either with the ethernet or the wireless (even though wireless shows it is connected, which I set up a second time), even though both are working with the other machines.

I am a Ubuntu novice and I have no idea how to troubleshoot or repair this and I cannot think of anything I did that was new or odd.  Any help will be very much appreciated.

---

### Post by s.fox on 2009-06-24
Hi and welcome to the forum :D, 

Can you tell us about your wif card?  Is it USB?  If it is can you run this command and post the output:

```
lsusb
```

-Ash R

---

### Post by csolomon on 2009-06-24
This is a laptop, no USB port for the wifi card.  But remember, it won't connect through the enthernet either.  I am stumped!

---

### Post by csolomon on 2009-06-25
Answered my own question: Ubuntu 9.04 includes a program that fouls up the network, apparmor; use synaptic package manager to remove it.

---

### Post by Ceedub2 on 2009-06-25
> **csolomon said:**
> Answered my own question: Ubuntu 9.04 includes a program that fouls up the network, apparmor; use synaptic package manager to remove it.

Is  apparmor used for anything important so my system won't work? Might be why my network wont work after suspending then resuming.

---

