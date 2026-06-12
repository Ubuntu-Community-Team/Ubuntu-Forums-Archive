---
title: "Ubuntu 1 Time Crash to BusyBox on Boot and Problem that Makes me say WTF."
date: 2009-04-21
forum: General Help
---

### Post by zigx on 2009-04-21
I had a crazy experience today but first some preface.

I recently built my computer and noticed that the HD light stays on permanently and that the DVD drive is not functional.

I assumed I just accidentally switched the HD's LED jumper which caused the light to stay on.  Also thought i may have forgotten to attach power to the dvd drive as i had been taking the computer apart and rebuilding it frequently.

That was 2 months ago -- yes 2 months :)


Today i booted up the computer and Ubuntu crashed.  A bunch of errors scrolled by too quickly for me to catch them and it dropped me into a busybox shell.

I realized the HD light was Off and just for the hell of it i tested the DVD drive and it opened.

Not knowing what to do with the busybox shell, i tried rebooting the computer and was able to successfully boot right back into Ubuntu like nothing had happened before.



My question is WTF could be causing the HD light to stay on and the DVD drive to not work while booted into a fully functional ubuntu install?  And how can i debug the crash?

Thank you!

---

### Post by northern lights on 2009-04-21
> **zigx said:**
> And how can i debug the crash?
Check ```
dmesg
```as well as```
/var/log/syslog
```

---

### Post by scottuss on 2009-04-21
Just an assumption here but based on what you have said, your DVD drive will not open when Ubuntu is running? But it opens during boot (BIOS stage) or when you get dropped into BusyBox?

---

### Post by zigx on 2009-04-21
> **northern lights said:**
> Check ```
dmesg
```as well as```
/var/log/syslog
```

I was never able to boot into ubuntu -- i looked through the logs but i didnt see anything that jumped out at me and im thinking maybe it's because ubuntu crashed before it got that far?

---

### Post by zigx on 2009-04-21
> **scottuss said:**
> Just an assumption here but based on what you have said, your DVD drive will not open when Ubuntu is running? But it opens during boot (BIOS stage) or when you get dropped into BusyBox?

Does not open during BIOS Stage, but that one time i was dropped into BusyBox it was able to open, lol.

---

### Post by scottuss on 2009-04-21
> **zigx said:**
> Does not open during BIOS Stage, but that one time i was dropped into BusyBox it was able to open, lol.

That's very strange! I don't even know where to begin trying to figure out why that is LOL.

Do you have another optical drive that you could replace it with, just to see if it is the drive's fault as opposed to motherboard / BIOS / cables etc etc

---

### Post by zigx on 2009-04-21
unfortunately i dont!  dang!

---

