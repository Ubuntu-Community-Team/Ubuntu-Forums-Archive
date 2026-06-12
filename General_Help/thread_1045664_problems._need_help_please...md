---
title: "problems. need help please.."
date: 2009-01-20
forum: General Help
---

### Post by Nova12 on 2009-01-20
okay so i have a problem, ubuntu wont let me save anything, half the programs wont work, mozilla juts exits itself all the time. i dont know what to do, and every time i go to turn off my computer my gnome panels disapear, and i have to hard shut down,. me one know aht to do? im am new to ubuntu, i love it but its irritating as hell.

---

### Post by cybergalvez on 2009-01-20
> **Nova12 said:**
> okay so i have a problem, ubuntu wont let me save anything, half the programs wont work, mozilla juts exits itself all the time. i dont know what to do, and every time i go to turn off my computer my gnome panels disapear, and i have to hard shut down,. me one know aht to do? im am new to ubuntu, i love it but its irritating as hell.

More info please, is this a new install? what is your hardware? is this new behavior? if not when did it start? what version of Ubuntu are your running?

---

### Post by DGortze380 on 2009-01-20
> **Nova12 said:**
> okay so i have a problem, ubuntu wont let me save anything, half the programs wont work, mozilla juts exits itself all the time. i dont know what to do, and every time i go to turn off my computer my gnome panels disapear, and i have to hard shut down,. me one know aht to do? im am new to ubuntu, i love it but its irritating as hell.

Step one. No more hard shutdowns. That's asking for trouble. Next time please try the following:

ctrl+alt+backspace  (will restart x and bring you to the log-in screen)

alt+f2   (should bring you to a terminal)

log in at the terminal

sudo shutdown -h now   (will shut down your computer)

---

### Post by Nova12 on 2009-01-20
> **cybergalvez said:**
> More info please, is this a new install? what is your hardware? is this new behavior? if not when did it start? what version of Ubuntu are your running?

well im running a dell p.o.s. it was just a computer given to me, and all this crap started after i updated ubuntu, i cant save anything on abiword. i dont think its my hardware, the last os i was running worked fine, its just been since i installed ubuntu. mozilla just closes itself, and wont let me save images, or anything.. but i really dont know what kind of hardware i have it looks liek a mix of a bunch of stuff. i know i have an Nvidia graphics card, but i dont know that much about computers. im trying to learn though. yeah unbuntu is a relatively new install for me, probly like 2 weeks ago,  got ne ideas what it could be or need more info?

---

### Post by cybergalvez on 2009-01-21
so it was working fine until a couple of weeks ago when an update messed it up, is that correct? so I'm assuming your running 8.10 right?

do you have any broken updates? you can use synaptic to check your broken packages.  Also since you have an nvida graphics card you which driver are you using? are you using the proprietary one (the current one in the repository is version 177)

---

### Post by jerome1232 on 2009-01-21
I'm going to vote that you disk is full, let's take a look and see can you post the output of these commands?

```
df -h
sudo du -hx --max-depth=1 /
```

---

