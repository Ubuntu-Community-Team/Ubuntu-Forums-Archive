---
title: "Beryl Stops me from starting..."
date: 2007-06-08
forum: Desktop Effects &amp; Customization
---

### Post by LollYouSuckZor on 2007-06-08
Well.. Since I installed beryl, for the second time, I've had issues with it.
Im using Edgy 6.10 Kubuntu.
I was wondering, how do I stop it from running on startup in recovery mode?...

Any time I start my computer, and load, I login, and BAM right into my crashed beryl.  Anyway to remove it/stop it in RECOVERY?  =[

---

### Post by Najand on 2007-06-08
Use:
```

killall beryl

```

---

### Post by LollYouSuckZor on 2007-06-08
Okay, so here's some more information about my problem.

When I startup normally, It will start beryl and I will have one chance to type something in the console before it jumps into the cube and im locked there, in a frozen screen.  I can still rotate however, nothing loads, but the console.  I wanted to REMOVE beryl, hopfully I can do it with this one chance.  I will however try to kill beryl as Najand said. :) Thanks.

---

### Post by LollYouSuckZor on 2007-06-08
Alright, it just says that no operations were killed.  I want to remove beryl, FULLY.  

can I do this in failsafe?

---

### Post by gbesso on 2007-06-08
Boot normally, when you get to the login screen click ctrl+alt+f1 and you will get to a virtual terminal, log in there and type sudo apt-get remove beryl beryl-core beryl-plugins 
Click ctrl+alt+f7 to get back to the login screen, login, and once you're in X again run synaptic and remove the rest of the beryl packages.

---

### Post by ykpaiha on 2007-06-08
reading your problem it seems  (to my opinion ) that your xorg.conf is not properly configured or you missed the right driver on your machine?
screen freeze looks often like this kind of missconfig.
(why not trying feisty?)
I hope it helps a bitI

---

### Post by LollYouSuckZor on 2007-06-08
> **gbesso said:**
> Boot normally, when you get to the login screen click ctrl+alt+f1 and you will get to a virtual terminal, log in there and type sudo apt-get remove beryl beryl-core beryl-plugins 
Click ctrl+alt+f7 to get back to the login screen, login, and once you're in X again run synaptic and remove the rest of the beryl packages.

Yes! Thank you SO much.  While going into the package manager, I realized I didn't request to install any of the beryl plugins, or Beryl-manager.

Let's try this again. :)

---

### Post by gbesso on 2007-06-08
You're welcome! Better luck this time I hope ;)

---

