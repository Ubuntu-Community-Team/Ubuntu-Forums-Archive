---
title: "xorg.conf messed up, i have no X"
date: 2006-01-04
forum: Desktop Environments
---

### Post by hopspitfire on 2006-01-04
I was getting video drivers for my ati card from the site because i didnt have 3d acceleration, and when I reboot it won't load X and tells me that the xorg.conf is messed up and it cannot find a monitor. My question is, how do I reinstall x11 and have it fix everything up the way it used to be? Thanks in advance.

---

### Post by Lambert on 2006-01-04
If you can boot into a console run this command.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

If you don't immediately see a terminal after booting try ctrl+alt+F1

---

### Post by crispy_420 on 2006-01-05
DId the ATI drivers install?

I have an ATI 9800 Pro and when I screwed up settings (and I have many times), I run fglrxconfig from terminal. 

Can you login still to terminal?

Try that worked for me in the past many times. From there you can setup all over again. And it saves settings to xorg.

As a side not, ATI drivers aren't that great yet in linux.

---

### Post by hopspitfire on 2006-01-05
Yeah, they installed and everything, oh well at least ati is trying (unlike many other vendors who won't shell out linux natives). I did the suggestions from the 1st post and im back up! I'm posting from ubuntu now :P Thank you for your help, and hopefully ati can get better at this.

---

