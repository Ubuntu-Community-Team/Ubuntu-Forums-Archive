---
title: "after KDE XFCE and XPDE instalation i can not get my login screen ??"
date: 2007-07-26
forum: Desktop Environments
---

### Post by Aamir Aziz on 2007-07-26
i've installed the KDE XFCE and XPDE in ubuntu 7.04 i did not restart my computer at that time than after 6 hours  i logged into KDE and loged out than what happened, i can not see the login screen just i can see only black screen and it looks that something is loading. i wait for 3 hours but nothing happened i restart my computer many times and also pressed ctrl-Alt-Backspace. after the sixth attempt i got blue screen with message
the message was:

[B]Display server has been shut down about 6 times in last 90 seconds. it is likely that something bad is going on 
waiting for 2 minutes before trying agaion on display.
[/B]

i wrote the error mesage on paper and pressed again ctrl-Alt-Backspace. than i got the new message written on black screen i.e.

[B]not staring k display manager
it is not the default display manager.
[/B]
 

how can i login ... i have live cd of ubuntu 7.04

---

### Post by NESFreak on 2007-07-26
<ctrl>+<alt>+<f1> gives you a cli.

reconfigure the x server by using```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by pbcartwright on 2007-07-26
under /etc/sysconfig look at windowmanager:

## Default:     kde
## Config:      profiles,kde,susewm
#
# Here you can set the default window manager (kde, fvwm, ...)
# changes here require at least a re-login
DEFAULT_WM="kde"

---

