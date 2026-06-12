---
title: "Flash in web broswer affects gameplay. (Gridwars)"
date: 2009-02-28
forum: General Help
---

### Post by jellylogix on 2009-02-28
After much troubleshooting, I have pinpointed the reason to many of my gaming issues. When I play GridWars in ubuntu, and if I have flash in my browser doing anything, then it will block sound from the game, and on top of that, Gridwars (played fullscreen) will terminate unexpectadly randomly while playing it, not even 10 minutes into the game. Has anybody else had this issue? and if so, have you found a fix?

- Ryan

---

### Post by thtrgremlin on 2009-02-28
Some games take sound errors as fatal exceptions. Personally, I think that is bad. The real problem is that different applications use different soound drivers, each of which have different effects on how the audio device is compromised. Preferably every application would be written to use pulse audio. Firefox does, but I would not be surprised if grid wars does not. If grid wars trys to grab the audio device with, say, oss, it will fail because pulse audio already has it. A couple things you can try:

Check grid wars to see if in the audio settings you can set it to pulse audio. Of course, try this without flash running. If not, set it to alsa, then launch the application using the command ```
padsp gridwars
```This will 'trick' grid wars into thinking that a pulse audio channel is actually is alsa, and pulse audio will handle the rest.

Pulse audio is the default sound system for Ubuntu, and while it is really awesome, not every program is setup to use it. Fortunately, firefox IS setup for pulse audio. :)

Hope that helps.

---

### Post by DarkDead on 2009-03-05
Thanks for the tip thtrgremlin. I had the same problem and running with: ```
padsp gridwars
``` does the job.

---

### Post by jellylogix on 2009-03-15
awesome thanks. this fixed both issues, sound and the fact it terminated without reason (which I learned was because of the sound drivers as well.)

---

