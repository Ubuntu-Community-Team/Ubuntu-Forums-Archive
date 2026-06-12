---
title: "powernow daemon issue"
date: 2005-11-12
forum: Desktop Environments
---

### Post by dpw2atox on 2005-11-12
Ive been having some weird problems with ubuntu, mainly performance issues and i was really confused why but today i was checking my /proc/cpuinfo and i saw that my processor was only running at 1Ghz not 2Ghz like it should. I found some instrucitons in the transgaming cedega 5.0 release notes on how to disable it and suddenly things are running so much nicer. I figured i'd share this with everyone here incase they are experiencing any problems and want to check to see if its happening for them also.


i fully removed the powernowd package and things are still running smooth.





In many Debian based distributions such as Ubuntu this can be done by:

To disable CPU frequency scaling by stopping the powernow daemon (as root): /etc/init.d/powernowd stop
To reenable CPU frequency scaling by starting the powernow daemon (as root): /etc/init.d/powernowd start
Please check your distribution documentation for how to set the CPU Speed for your computer.

---

### Post by Mayfairy on 2005-11-14
Thanks! 
I noticed my AMD Athlon 64 3000+ processor was running on 1000MHz instead of 1800MHz it was supposed to. 'Powernowd stop' corrected it.

---

### Post by Hallavej on 2005-11-14
powewnowd only reduce cpu speed when you dont need it. Try to make your computer work hard (a hard calculation or run a virus check) and you will see that your cpu speed has the correct value.

---

### Post by dpw2atox on 2005-11-14
it wasnt working properly for me though and the cpu speed stayed at 1Ghz even when playing a game or anything. I have greatly improved my system performance in general and espcailly with games.

---

### Post by Hallavej on 2005-11-14
[QUOTE=dpw2atox]it wasnt working properly for me though and the cpu speed stayed at 1Ghz even when playing a game or anything. I have greatly improved my system performance in general and espcailly with games.[/QUOTE]

I am starting to agree. My cpu speed does indeed change to 2Ghz but only when i really push it. I dont play games but after turning it on and off a few times I think that some programs are a bit faster without powernow. I dont see a great improvement in my system performance, just a small one.

---

