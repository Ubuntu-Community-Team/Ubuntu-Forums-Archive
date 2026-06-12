---
title: "What is the process name of zsnes?"
date: 2009-04-14
forum: Gaming &amp; Leisure
---

### Post by mister_playboy on 2009-04-14
It has me trapped in 640x480 without a mouse, and I need to kill the process.  :(

---

### Post by mister_playboy on 2009-04-14
Never mind.  I couldn't kill it because it wasn't actually running.  Opening zsnes again got me my mouse back, then I had to manually change the screen resoluton.  Conviently, OK is always somewhere at the bottom of the window, which you can't see in 640x480...

Zsnes constantly pulls this crap on me in Linux... what a PITA.

---

### Post by dfreer on 2009-04-14
It should be the name zsnes, unless you renamed the binary differently, in which case it would be whatever name you renamed it to.

If you have terminal access, you can use top/htop in order to view a list of running processes if you are unsure of it's name, with htop you can send it a kill signal from there as well.

You can also try an <Alt>+<Enter>, it should bring the application out of full screen. Manually editing the ~/.zsnes/ cfg file and changing the resolution, then launching ZSNES should also help any resolution issues you may be having. Not sure why the mouse isn't working for you though.

---

### Post by kdorf on 2009-04-15
I always run zsnes in a separate X server to avoid exactly the problem you describe. Then my mouse doesn't die on me if something bad happens. =)

---

