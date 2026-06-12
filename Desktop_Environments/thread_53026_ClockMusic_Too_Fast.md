---
title: "Clock/Music Too Fast"
date: 2005-07-29
forum: Desktop Environments
---

### Post by jpoe on 2005-07-29
First, I apologize if the solution to this has been posted elsewhere, but so far I have been unable to find it.

I have an AMD X2 4400 and I downloaded and compiled my own kernel 2.6.12.3 because it takes advantage of dual cores (previously I used the 2.6.10 k6 SMP but only 1 CPU showed up, and with the 12.3 both show up and a few multithreaded benchmarks i wrote and tested finish in half the time).  Since installing it (I have to use the noapic kernel option for it to load), whenever I use the CPU, it speeds up my clock *alot* ... like double real time.  At first, this wasn't too much a problem, i just resync'ed my clock with the time server every hour.  It has become more of a problem, however, since I began using KDE over Gnome.  While in Gnome only my clock and key repeate rate sped up, in KDE it also speeds up my music (MP3s). I found a few posts saying to try different kernel options (I can't remember them exactly now, no lapic and no timer something); but so far none of them have worked.  Does anyone have any idea what might cause this problem, or how to go about fixing it?  I could go back to the standard 2.6.10 kernel and solve the problem; however I would like to take advantage of both cores...

Also, on a slightly related issue; I have to compile NVIDIA modules from source for X11 to work (since restricted modules are not yet available for 2.6.12.3), which isn't a problem.  However for some reason I have to recompile and install these on *every* reboot.  It works fine after I do it, however they aren't persistent.  Is there any reason for this?

Thanks for all the help I've been given so far, and any help with this issue,

**EDIT ADDED**
Btw, this happens for all sound daemons that I use (ALSA, OSS, and OSS Threaded .. for some reason Enlightened gives an error ...)

---

### Post by jpoe on 2005-08-01
err, anybody have any ideas about this?

I'm fairly confident (ah man I hope) this will all be resolved by the time breezy comes out in October, but I've grown so fond of ubuntu that I don't want to have to return to windows even that long... 

...if any additional printouts (dmesg,lsmod, shrug .. I'm still a noob) would help, I'll be glad to post..

thanx

---

