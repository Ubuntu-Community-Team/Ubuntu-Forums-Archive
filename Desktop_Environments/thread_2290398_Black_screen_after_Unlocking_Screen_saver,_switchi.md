---
title: "Black screen after Unlocking Screen saver, switching user or just logging after boot"
date: 2015-08-12
forum: Desktop Environments
---

### Post by dealy663 on 2015-08-12
I've been having these problems on my XUbuntu 15.04 machine. It happened a lot when I first installed, then I some how fixed the problem and that lasted for a month or so. Now it is back with a vengence, and I cringe every time my screen locks or I have to switch users. I never when my computer is just gonna be a black screen after I login and then I'll be forced to do a hard reboot. When this happens I can't use Ctrl+Alt F1 2 3 or whatever, there is just no response. 

My machine is a Lenovo Y50 with an Nvidia 860 card. I've tried messing with lightlocker settings to no avail. How can this be such a common problem on a modern OS? I know my system hasn't crashed because the keyboard lights are still controllable, and the caps lock and num lock indicators respond.

Any suggestions on how to make this problem go away would be really appreciated.

Thanks, D

---

### Post by workshopsystems on 2015-08-13
```

xset -dpms s off s noblank s 0 0 s noexpose

```

run that in a terminal and leave the computer running if the screen doesnt go blank then add that to the startup

---

### Post by dealy663 on 2015-08-14
That didn't really do the trick.

I know the computer is still running. Isn't there something I can at least do to salvage the situation that doesn't require a hard restart and me to loose everything that was being worked on. This is so massively frustrating.

---

