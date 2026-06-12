---
title: "Fluxbox Menu Error?"
date: 2009-01-19
forum: General Help
---

### Post by uzdrowic36 on 2009-01-19
Hi guys, I'm a bit new to Ubuntu and the forums but I've used Linux for almost a year now, but only recently last month decided to delve into Fluxbox. I tried out the Fluxbuntu distro on a virtual machine running under Windows XP SP3, and loved it. So I'm currently about to install Ubuntu via Wubi onto my machine, but before so, I tried a virtual machine, put Ubuntu 8.10 on it, installed Fluxbox, and when I logged into the Fluxbox session, it was fine for a minute. Then, the desktop icons I had set from GNOME appeared, and knowing from online sources that you normally can't have desktop icons without a special file manager such as ROX, got nervous. Sure enough, a couple seconds after I opened Nautilus, (that's the most comfortable file browser for me, I didn't know which to pick) I tried right clicking on the desktop, and the default GNOME right click menu appeared, not the Fluxbox menu! Is this a problem caused by the desktop icons, Nautilus, or another source? Please respond because I'd like to have Fluxbox running smoothly on my Wubi install.:-|

---

### Post by snowpine on 2009-01-19
To invoke nautilus without messing up your desktop, try this command in your fluxbox menu or from the terminal:

```
nautilus --no-desktop
```

You might consider using a more fluxbox-friendly file manager. I personally like thunar and pcmanfm. :)

---

### Post by uzdrowic36 on 2009-01-19
Thanks, I'll try that, but I'm thinking of moving onto ROX. :) Just to clarify, it was Nautilus that was causing the problem? Thanks for your help! :KS

---

