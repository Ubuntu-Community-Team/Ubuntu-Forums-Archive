---
title: "sound card setup"
date: 2006-06-22
forum: Desktop Environments
---

### Post by foxhound_oki on 2006-06-22
i need help setting up my sound card drivers.  i have via sound card on the motherboard.  i need to obtain the drivers and get them installed so i can have sound.  i have been without sound since installation.  i have reinstalled ubuntu but did not work to fix my sound problem.  please some one help me.:)

---

### Post by Ctrl+Alt+Del on 2006-06-22
There's mostlikely no need to obtain third party drivers, check your devices name by typing lspci into a console. you will mostlikely get an output like
```
02:03.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
```
With that info you can go to [http://www.alsa-project.org/alsa-doc/](http://www.alsa-project.org/alsa-doc/) and look up the required kernel-module (aka driver). From there on, you can follow
[https://help.ubuntu.com/community/HowToSetupSoundCards](https://help.ubuntu.com/community/HowToSetupSoundCards)
The wiki article is a bit short, but it should get you to a point where you can ask about specific issues if sth goes wrong

---

