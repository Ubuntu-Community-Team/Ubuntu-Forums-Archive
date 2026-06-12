---
title: "Firefox 3.0.10"
date: 2009-05-03
forum: General Help
---

### Post by sbentjies on 2009-05-03
It would appear that Mozilla has not patched their browser for Ubuntu. Their latest release still crashes regularly. Granted I'm running on older hardware but this is RIDICULOUS. Can anyone tell me how to kill Firefox when it crashes?

---

### Post by RedSingularity on 2009-05-03
I have not had any problems with firefox........anyway go to
System>admin>system monitor.  Look for firefox and kill it.

---

### Post by Wheels8257 on 2009-05-03
From the command prompt:

sudo ps -e | grep firefox

This should return "firefox" and the process ID.

If it does, type in

sudo kill <process ID>

Without the < >.

Wheels8257

---

### Post by Just_SomeGuy on 2009-05-03
> **Wheels8257 said:**
> From the command prompt:

sudo ps -e | grep firefox


An even easier way I just happened upon:
pkill firefox

---

### Post by Wheels8257 on 2009-05-03
> **Just_SomeGuy said:**
> An even easier way I just happened upon:
pkill firefox

Didn't know about that. Pretty neat.

---

### Post by lovinglinux on 2009-05-03
> **Just_SomeGuy said:**
> An even easier way I just happened upon:
pkill firefox

or simply

```
killall firefox

```

---

### Post by sbentjies on 2009-05-03
Hey guys, thanks for the great response. Reasons for Firefox crapping out seem to vary from a script not loading on a page to it just choking. Any suggestions as to how to give FF and edge here would be appreciated. I especially like pkill. That's cool. Again, thanks to all.

SB

---

### Post by zero7404 on 2009-05-03
i love posts like this, open my notepad and jot down all the commands for future reference....

i use the force quit icon, but sometimes the firefox window is closed and when i try to start it i get the message saying that it's still running and needs to be killed....but when there's no visible window, force quit doesn't work.

---

### Post by sbentjies on 2009-05-03
Mostly I get it grayed out where it's locked up-it is non-responsive. Where is the force quit icon? I can't seem to remember the keystrokes.

---

### Post by zero7404 on 2009-05-04
> **sbentjies said:**
> Mostly I get it grayed out where it's locked up-it is non-responsive. Where is the force quit icon? I can't seem to remember the keystrokes.

i think i found it under sessions, i don't remember exactly, if it's not there maybe check synaptic to make sure it's installed....

it's called wallpaper-tray
you can manually add it to sessions/startup programs easily, as the command is just 
```
wallpaper-tray
```

---

