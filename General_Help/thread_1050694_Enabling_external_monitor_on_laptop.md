---
title: "Enabling external monitor on laptop"
date: 2009-01-25
forum: General Help
---

### Post by jumboshrimp11 on 2009-01-25
I bought a new monitor, and am trying to hook it up to my laptop, which unfortunately has a broken screen. So, When I turn on my laptop with the monitor plugged in, I can see everything on the monitor... until it moves to the login screen, where the monitor goes blank. I don't know what i could do, because my laptop monitor is broken. Does anybody have any ideas? Thanks!

---

### Post by jonkulp on 2009-01-25
I'm not sure how easy it'll be if you can't see what you're typing, but you might try using the xrandr tool to flip the output to the external monitor.  When I want to use a projector I type this command:

```
xrandr --output VGA --mode 1024x768
```

If you substitute the appropriate resolution for your monitor it should look o.k.  I can't remember if xrandr comes in the Kubuntu desktop or not, but you can apt-get it if it's not already installed.  I guess the hard part will be logging in and getting to a command line without being able to see it. Good luck :)

---

### Post by abn91c on 2009-01-25
on your laptop press the fn key and depending on brand f3 or f5 sometimes f8 to toggle between the lcd and the external monitor, look at the keyboard for the f key with the monitor icons

---

### Post by jumboshrimp11 on 2009-01-25
Unfortunately, the function keys on my laptop have never worked under linux, so i can't take that route. Does anybody know how i might access the terminal without just guessing where to find it? because guessing is not working so well :S

---

### Post by jonkulp on 2009-01-26
Can you access the system BIOS while you can still see the bootup process on the external monitor?  If so, then perhaps you could go in there and change the display preferences from the built-in LCD to the external monitor.  I had to do this on my old Dell laptop before I could get it to work with an external monitor.

---

### Post by jonkulp on 2009-01-26
> **jumboshrimp11 said:**
> Does anybody know how i might access the terminal without just guessing where to find it? because guessing is not working so well :S
You're doing this blind so you have to type carefully, but it doesn't rely on graphical interface so it might work. Do Alt+F2 to open up the launcher, then type "xterm" and return.  The terminal should be open at this point and you could try the xrandr command from there.  If you think you hit the wrong command or nothing happens, do Ctrl+C to get the prompt back and try it again.

---

### Post by jonkulp on 2009-01-26
Here's another idea: ORCA, the screen reading app for visually impaired.  Once you're logged in, hit Alt+F2, type "orca" and hit enter.  You'll hear it welcome you.  Hit Alt+F2 again and type "xterm" to launch the terminal.  Orca tells you every keystroke you're doing.  Maybe that'll help get the external monitor set up.

---

### Post by ussndmac on 2009-01-26
Is the laptop on a network?

Maybe you could login remotely, do what ever config you need to get the external monitor to be the default display?

---

