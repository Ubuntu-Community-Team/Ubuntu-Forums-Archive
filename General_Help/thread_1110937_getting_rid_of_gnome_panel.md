---
title: "getting rid of gnome panel"
date: 2009-03-30
forum: General Help
---

### Post by profeta81 on 2009-03-30
Hello

sorry for the silly question,

I once started nautilus from command line while using xfce. This changed all the xfce settings into the gnome ones (desktop, colors, icons etc). after logout and login again xfce preserved the gnome settings instead of reverting to the original ones, so I looked into the gnome-system-manager and killed manually nautilus which was still running. Now xfce doesn't shows the icons anymore on the desktop and it doesn't let me access the xfce menu by right clicking on it...

does anybody know how do I revert to the original settings

cheers

---

### Post by j7%&lt;RmUg on 2009-03-30
Ok im going to have a go but iv never used xfce before so i may not be right. If its what i think it is then this happens to my GNOME session sometimes. To fix it logout and go to sessions which will be somewhere on the login screen. Once you are there just change it back to whatever you want click OK and log back in.

If this does not do anything then im sorry but i dont know.

---

### Post by profeta81 on 2009-03-30
> **nisshh said:**
> Ok im going to have a go but iv never used xfce before so i may not be right. If its what i think it is then this happens to my GNOME session sometimes. To fix it logout and go to sessions which will be somewhere on the login screen. Once you are there just change it back to whatever you want click OK and log back in.

If this does not do anything then im sorry but i dont know.

well, thanks for the reply, but this is not the problem. I'm selecting the right "session type" (xfce) but when I started nautilus, it read all the gnome configuration as well, and now, after I killed nautilus using gnome-system-monitor, all the desktop items have gone...

---

### Post by j7%&lt;RmUg on 2009-03-30
Try a reboot and see if that helps. Apart from that i have no idea whats wrong since i dont use XFCE.

---

### Post by profeta81 on 2009-03-30
> **nisshh said:**
> Try a reboot and see if that helps. Apart from that i have no idea whats wrong since i dont use XFCE.

Thanks, again that didn't solve the problem too :)

Yet, I did solve the problem anyway: on the xfce setting manager, under the voice "desktop" there is the option "let xfce manage your desktop", once that was ticked again everything worked fine again

thanks for the help anyway

L

---

### Post by mkvnmtr on 2009-03-30
Right click on the desktop in your xfce session and see if a window pops up that asks if you wish to let xfce manage your desktop. Later when I have time to switch to a xfce session I will check this advise but this is how I remember it.

---

