---
title: "How to make a network bridge?"
date: 2006-06-23
forum: Desktop Environments
---

### Post by Stex on 2006-06-23
I feel pretty dumb right now, I've searched around, read everything about the subject but can get no further than downloading Bridge and then have no idea what to do next. Can anyone write a detailed howto? I need to give my wireless connection through an ethernet lead. Both computers in question are running ubuntu 6.06

The main problem I'm having right now is how do I install Bridge from the archive I downloaded?

I tried ./configure but I get the error:
> configure: error: no acceptable C compiler found in $PATH

---

### Post by mips on 2006-06-23
I don't really understand what you are saying but it sounds like you want to share an internet/network connection ??? If this is the case just install Firestarter from synaptic and enable internet connection sharing from within Firestarter.

---

### Post by Stex on 2006-06-23
Thank you, I was indeed looking at the entirely wrong thing as usual :)

If anyone's wiling to help:
I've set up the Internet sharing as instructed on the firestarter help site exactly (though without dhcp) but it just isn't working. Both computers have been connected to a router using this cable successfuly so I don't blame the hardware.

Hmm... actualy, am I meant to be using a patch cable or a crossover cable?

---

### Post by mips on 2006-06-25
[QUOTE=Stex]Hmm... actualy, am I meant to be using a patch cable or a crossover cable?[/QUOTE]

Yes, a crossover cable ! You always use a crossover cable between the same devices.

---

### Post by drpaul on 2006-06-25
if you have a router, then if it is connected to your modem that connects to internet, i wouldn't think that there is much more for you to do [if your wireless connection to the router is working].

if your other machine is connected to the modem, then the firestarter thing ought to work for you.

???

paul

---

