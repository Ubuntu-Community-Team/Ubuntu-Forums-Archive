---
title: "Autostart scripts for KDE for all users?"
date: 2005-10-16
forum: Desktop Environments
---

### Post by cwaldbieser on 2005-10-16
I just upgrades to Breezy from Hoary, and most of the upgrade went pretty smoothly.  One small glitch I am experiencing is with my sound under Kubuntu.  

I have a sound card built into my motherboard, but it is not Ubuntu-friendly, so I installed a second sound card in the computer.  In Hoary, I added an rc.local script in /etc/init.d that ran
```

esd -d /dev/dsp1

```
and everything worked fine.  After the upgrade, it seems like only the user that initiated the esd command can connect to it, so root running esd from my startup script no longer works.

I can run the command myself from the terminal, and everything works fine again, but it is somewhat annoying to have to keep doing this.  I tried putting it in my ~/.kde/Autostart folder, but this apparently gets run *after* KDE tries to initialize the sound system.  

I am looking for a way to run the script as the user who is trying to start a KDE session before KDE goes through its startup process.  I guess I could rename "startkde" to "startkde.bin" and create a front-end script to do the job, but I figured there is probably already some config file I can use for this purpose.  I tried .xinitrc, .xsession, .xprofile, and none of them seemed to do the job.  Does anybody have any ideas?

Thanks.

---

### Post by CAE on 2005-10-16
I just wrote a [HOWTO](http://ubuntuforums.org/showthread.php?t=76978) for configuring multiple soundcards under Kubuntu. Hopefully it can help you.

---

