---
title: "just dual booted linux and XP, linux not logging in"
date: 2009-02-17
forum: General Help
---

### Post by luke904 on 2009-02-17
HI

I just installed (dual boot with XP)ubuntu 8.10 on my dell dimension 2400 (2.4 GHz celeron, 512 MB ram, 400 MGz FSB, crappy integrated intel extreme graphics). It worked great until i tried to log into ubuntu and it just sat there with a orange-white screen and a mouse curser, the hard drive wasnt doing anything and i left it there for 3 days once and nothing happened.

any ideas?

---

### Post by mozkill on 2009-02-17
boot to a "LIVE Ubuntu" dvd and then if you can access the XP drive then the drives are ok.

i suspect ubuntu is having a problem with how you have setup the hard drives in the BIOS.  you should try setting your hard drive to IDE mode instead of SATA mode.  

when installing Ubuntu if you are seeing it not respond during install, then it could also be a bad sector in your memory/RAM .   make a copy of CloneZilla and boot from it and run the memtest  that is on it.

---

