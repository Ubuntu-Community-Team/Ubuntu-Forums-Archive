---
title: "Blank Screen! GDM won't show up! Doom! Despair! What Do I Do?"
date: 2011-04-29
forum: Desktop Environments
---

### Post by OldTimeyJunk on 2011-04-29
Hello!
Recently I installed the Matchbox desktop enviroment to try it out as I was going to use it on an embedded device (not any more though). When I Rebooted my PC, Matchbox came up (I didn't need to login). I unistalled Matchbox on Matchbox (and watched it break), restarted my PC and now GDM (Login manager) and Gnome won't show up after booting giving me a completely blank screen.

I'm on Ubuntu 10.04.2 LTS.

What Do I Do?

PLEASE HELP!!!

Josh Robertson

---

### Post by Krytarik on 2011-04-30
Try reinstalling "gdm":
- boot into "recovery mode -> root shell prompt with networking"
- run:
```
apt-get install --reinstall gdm
```[INDENT]Note: No need to use 'sudo' because you will already be root.
[/INDENT]- reboot by pressing Ctrl+Alt+Del

Greetings.

---

### Post by OldTimeyJunk on 2011-05-02
Too late! I figured it out. I booted up in Failsafe Ubuntu and it worked by starting X.

---

### Post by Krytarik on 2011-05-02
> **OldTimeyJunk said:**
> Too late! I figured it out. I booted up in Failsafe Ubuntu and it worked by starting X.
"startx", why not?! ;-)

See here if you want to always boot to the CLI instead of GDM, but without the need to choose "recovery mode":
[http://ubuntuforums.org/showthread.php?p=9644518#post9644518](http://ubuntuforums.org/showthread.php?p=9644518#post9644518)

---

