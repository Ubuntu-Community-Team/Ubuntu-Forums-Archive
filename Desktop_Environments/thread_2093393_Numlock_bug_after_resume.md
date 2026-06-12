---
title: "Numlock bug after resume"
date: 2012-12-10
forum: Desktop Environments
---

### Post by netrick on 2012-12-10
So, when I suspend my pc (sleep, don't know how to translate it, but it's not hibernate but the second option, with ram being powered) and then resume it, I have a very strange behaviour.
Before suspending, I have numlock turned on. I suspend it then I resume my pc. Then, here is the bug:
- numpad is working, from software-side numlock is enabled
- BUT on my keyboard, numlock LED is turned off

It isn't critical bug, but it looks a bit strange and I'd prefer to have that numlock behave correctly when suspending.

I'm using lubuntu 12.10.

Thanks

---

### Post by Statia on 2012-12-10
Same bug here in Kubuntu 12.04.
Numlock is on, but the light isn't. Pushing it twice fixes it: first time nothing happens (I turn of a light that is already off), second time it comes on.
Related: after resuming from sleep I have to run the script again to make my winkey call the KDE-menu. Script is located in ~/.kde/Autostart.

---

### Post by netrick on 2012-12-10
Yes, I have the same behaviour with pressing it 2 times to get led working.
Is this bug known to devs?

edit:
I use numlockx to have numlock enabled after boot. I guess there should be something done that start-up scripts are executed after resume.

---

### Post by Statia on 2012-12-12
> **netrick said:**
> 
Is this bug known to devs?


I never found this important enough to file a bug report for or check if there is an existing bug report, but I did post about it here before.

---

### Post by netrick on 2012-12-15
I think I know how to solve it. There are resume scripts in linux and we just need to put numlockx there to execute (maybe 2 times?). But I don't know anything how to find this script, do you have any clue?

---

