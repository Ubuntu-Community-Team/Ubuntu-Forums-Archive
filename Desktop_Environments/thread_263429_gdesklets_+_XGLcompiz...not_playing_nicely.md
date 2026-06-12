---
title: "gdesklets + XGL/compiz...not playing nicely?"
date: 2006-09-23
forum: Desktop Environments
---

### Post by kaisa on 2006-09-23
Just recently installed ubuntu and things are beginning to go more smoothly. XGL/compiz are up and running...wine seems to be doing its job for the most part. 

Anyway, I decided my desktop needed even more spice (like it does with XGL installed... :rolleyes: ) and decided to go ahead and install gdesklets. I just popped open synaptic downloaded it though there. Everything was working fine, and I was able to put desklets on my desktop...but the desklets seem to be constrained to the top half of my screen only! I hit a point on the screen where i cant drag them any further and they being to shake quite rapidly. If i flick the mouse up quickly to the top of the screen and then pull quickly down to the bottom, I get it to shake so violently that I can click when its at the bottom of its shake (its luck mostly) and get it to stay down at the bottom of the desktop.

Obviously something is wrong, and it shouldnt be doing that. The only thing i can think of that could be interfering is XGL. If I could figure out where the positioning of the windows is kept, I could just manually edit the file to get the windows positioned how I want, but that just seems silly. 

Hopefully someone who has experience with this program can help out. In the meantime I'll try using gdesklets without XGL/compiz running and see what that does...

Thanks!

---

### Post by LosD on 2006-09-23
I've also had problems with Compiz and desklet's... Mine wasn't the same (They got their position wrong on restarts), but it was related to the Compiz Minimize plugin, maybe try to see if it's also that one screwing with your desklets.

If not, then try to disable most of the plugins, and if dekslets work as they're supposed to, then enable them one at a time.

---

### Post by _simon_ on 2006-09-23
I came across this same problem yesterday.

I had to switch back to metacity to be able to drag the desklet to the position I wanted and then switch back to Compiz.

If you are using Quinn's then you can just click on your red cube in the task tray and switch window managers that way.

---

### Post by kaisa on 2006-09-23
It appears it was compiz causing the problems...looks like it should be alright now. Thank you for the quick replies (and info!). :cool:

---

