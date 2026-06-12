---
title: "Unbelievably and unacceptably poor performance"
date: 2009-01-16
forum: General Help
---

### Post by thoughtcriminal on 2009-01-16
My machine is acting horrifically slow whenever I try to run anything even remotely processor intensive. 
Running an GBA emulator runs one of my processor cores at 100%, the other at about 30%.
Running Runescape runs them both at 100% and chugs like crazy
I can barely even run Nexuiz.

Now, I know I don't have the best hardware ever: a core2 duo at 1.8ghz, 1 gb of ram (linux says I have 2gb for some reason), and a Geforce 8400M GT.

But I was doing all these things in vista with no slow down. Hell, I could even run Half Life 2: Lost Coast at near max settings.

What is wrong here? I have the nvidia drivers. I tried setting my cpu governer to performance. And my pc still lags like hell. 

I'm almost tempted to thing its because I'm running 64 bit, but I used to run 64 bit Hardy in Dual boot and that was exponentially faster, beating my Vista frame rates in Nexuiz with the same settings. (And I had compiz running on it too)

Vista, stripped down: 30fps
Hardy, with Compiz: 36 fps
Xubuntu intrepid, stock: <1 fps

anyone know whats up here? I could really use some help
thanks in advance
tc

---

### Post by thoughtcriminal on 2009-01-17
Any details that might be needed, please let me know

---

### Post by DeMus on 2009-01-17
> **thoughtcriminal said:**
> Any details that might be needed, please let me know

Did you look in the System monitor to see if there is a process running which is using the capacity of your processor?

---

### Post by upchucky on 2009-01-17
are u running intrepid? there were issues with intrepid and nvidia on release, there are ways to fix the issues since then, but i have not tried them cause i chose to wait for the next lts release of ubuntu instead.

---

### Post by thoughtcriminal on 2009-01-17
Yes I have checked the system monitor and total normal load is about 5-10% (running my normal programs: firefox, screenlets, pidgin, and listen). My screenlets show a slightly higher average, about 7-12%.

Yes, I am running intrepid. I am running the Nvidia driver version 177.82 if that helps.

---

### Post by 3rdalbum on 2009-01-18
Okay, well it's normal for games to use 100% of a core or of your CPU.

XFCE has a compositing window manager; have you tried turning off the compositing? Or if you're using Compiz, try switching to Xfwin as your window manager without compositing.

---

### Post by thoughtcriminal on 2009-01-18
> **3rdalbum said:**
> 
XFCE has a compositing window manager; have you tried turning off the compositing?

This was it. I'll be honest, I didn't really think about this. When I turned the compositing on, I watched the cpu usage and saw minimal difference at idle with it on and off.

Nexuiz now pulled off over 45 fps with the same settings. I even got to crank things up, to now all but maxed out levels, and am still running 26ish fps

Damn, I really liked my shiny. Well, I did have good luck with compiz before...

Thanks so much mate. And thanks to everyone who helped

edit: ok I'm feeling a little stupid here, as it is 4 am here and I'm a little tired. Didn't there use to be a way to mark a thread as solved? I can't seem to find it now...

Further edit: I now have Compiz up and running. It is far faster than Xfwm. I would really recommend all Xubuntu guy us Compiz instead of Xfwm

---

