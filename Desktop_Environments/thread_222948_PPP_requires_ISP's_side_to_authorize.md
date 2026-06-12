---
title: "PPP requires ISP's side to authorize?"
date: 2006-07-25
forum: Desktop Environments
---

### Post by nekr0z on 2006-07-25
I have had a great problem setting up my dialup: KPPP didn't connect, claiming that the remote machine (my ISP, I guess) didn't supply any valid password. Actually, that was MY machine that was to provide a password, but somehow it wanded ISP to authorize instead.

After having smoked up a huge pile of man pages and web resources I have finally uncommented the «noauth» option in /etc/ppp/options, and the whole thing started to work.

It was working until I tried to dialup from my home (I have a wireless network at home with no Internet gateway at the time). PPP reported the same error as before!

This time no man smoking or web surfing helped, but it turned out in experiment, that switching off all the network interfaces («sudo ifconfig ethX off») I have finally got online via dialup, but as soon as I switch on any ethernet adapter, PPP starts acking for a password from the ISP.

Does anybody have any idea of what is going wrong or have any link to read on this problem? Please share!

---

