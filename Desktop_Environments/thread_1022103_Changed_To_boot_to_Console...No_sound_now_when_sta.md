---
title: "Changed To boot to Console...No sound now when starting x server"
date: 2008-12-26
forum: Desktop Environments
---

### Post by sloanwolf on 2008-12-26
I ran this command sudo update-rc.d -f gdm remove to make my machine boot up to the console instead of kde.  It worked great except that now i have no sound when i launch kde from the console.  Amarok also gives me an error "xine was unable to initialize any audio drivers."  The weird part is if i open a console in kde and use sudo [program] i have sound with whatever program i launch that way, but i do not have sound when i launch the program without admin rights....very weird.  Any help would be appriciated.  And my sound card is Intel ICH7.

---

### Post by automaton26 on 2009-01-02
I tried this with a kubuntu 8.10 machine recently, although I did it by using "sudo sysv-rc-conf" (which needs installing first) and unchecking *kdm* for all runlevels 2 thru 5.

Doing "startx" gives problems with sound & power manager access.
Doing "sudo startx" seems to work, but I wouldn't want to run kde as root.

Would doing "/etc/init.d/kdm start" be better perhaps?

---

### Post by theozzlives on 2009-01-02
> **sloanwolf said:**
> I ran this command sudo update-rc.d -f gdm remove to make my machine boot up to the console instead of kde.  It worked great except that now i have no sound when i launch kde from the console.  Amarok also gives me an error "xine was unable to initialize any audio drivers."  The weird part is if i open a console in kde and use sudo [program] i have sound with whatever program i launch that way, but i do not have sound when i launch the program without admin rights....very weird.  Any help would be appriciated.  And my sound card is Intel ICH7.

crazy idea off the top of my head, why don't you try sudo startx?

---

