---
title: "modum not recognised"
date: 2009-04-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jim williams on 2009-04-18
Have just installed xubuntu on my Dell dimension 3000 dialup
and it will not recognise modum!!Have directly installed to h/d
and will probably need new modum ? if so could anyone advise on a
cheap dialup modum obtainable in Newzealand ?
             Many thanks
                     Jim

---

### Post by coffeeaddict22 on 2009-04-18
Hi,
Welcome to Ubuntu! 
The modem may well work with Ubuntu, if you're prepared to play a bit.  You're welcome to ask, lots (we all did once), and there's plenty of people prepared to help if you're prepared to try to get it going.  modems tend to be fairly generic in their input and output; they interface with the 'net through a standardised phone line and with the PC through a ethernet cable, so it's quite possible it's not a "modem" problem but a networking issue.

 Compatibility with Linux, paradoxically, is often better with slightly older gear; if the manufacturer doesn't release a Linux driver it takes a little time for the clever people to make one, but stuff that's been around a while tends to be supported better in Linux than any other OS.

If you're prepared to have a go at getting your current modem working, a few more details.  Is it hardwired or is there a wireless link somewhere?  Exactly what is or isn't happening?  Most usefully, type into a terminal (Applications/Accessories/Terminal) ```
lshw -C network
```
and post the stuff that comes out back here.

---

