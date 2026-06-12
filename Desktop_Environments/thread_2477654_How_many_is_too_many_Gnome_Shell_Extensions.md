---
title: "How many is too many Gnome Shell Extensions?"
date: 2022-08-02
forum: Desktop Environments
---

### Post by mickee384 on 2022-08-02
Is there such a thing as too many Gnome Shell Extensions? Is the only negative result of too many an increase in RAM used by gnome-shell? Or can they cause instability? I have 26 running as of today. Performance of the shell is fine. Just curious if using too many can affect the system? Like maybe if gnome-shell starts using over a GB of RAM after about 2 days after a reboot? I'm trying to narrow down the reason that sometimes after a couple of days I find that I can no longer unlock my system and it just has a very dark but also purple screen. Logging out or reboot fixes this, for a couple of days. I have tried disabling all the extensions, but still have issues when trying to unlock the computer. If it gets like this I have to go to tty and reboot - the only fix.

---

### Post by #&amp;thj^% on 2022-08-02
Gluttony has it's pitfalls. ;)
If I remember right the Max I ever used was around 12-15. (I don't use Gnome any longer)

You'll take a performance hit during startup if you have numerous gnome-extensions and depending on what the extensions do, may pay performance penalty during run time but beyond Ram and swap space limiting the amount of gnome-extensions that can run concurrently, you should be able to run many gnome-extensions.

---

### Post by ActionParsnip on 2022-08-03
Depends on the system. The OS will run as much as it can on the resources available. A system with 512Gb RAM will run more applications (and more extensions) than one with 1Gb RAM

---

### Post by mickee384 on 2022-08-04
Thanks for your input. I have disabled all but 2 in my efforts to determine why my system doesn't come back after unlocking my pc. It sometimes just comes up with just a dim purple screen, like just a dim backlight, requires logout, reboot or lately I figured out on tty killalll -3 gnome-shell, then log in under CTRL+ALT+F1. It has been doing this since I upgraded to 22.04. If disabling the extensions doesn't fix it, I will do a fresh install in a few weeks..

---

