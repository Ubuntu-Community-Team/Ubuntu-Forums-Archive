---
title: "Can't log off"
date: 2007-04-19
forum: Desktop Environments
---

### Post by Old Pink on 2007-04-19
Metacity closes, panels close, nice full screen wallpaper, computer frozen. Tried it all, won't even kill X or quit to terminal. 

Thanks to Feisty. I never get a shutdown splash either. 

I sure miss Edgy... same main features, no breakage... had thought this would be fixed in final release.

---

### Post by Old Pink on 2007-04-20
One day later... no reply?

---

### Post by s_p_a_r_k_y on 2007-04-20
ctrl-alt-X should be able to kill the X server. Also you can shut town computer from the command line by using ctrl-alt-f1 (ctrl alt f7 bring you back to graphical) and logging in then typing in reboot or shutdown (or to restart graphical sudo /etc/init.d/gdm restart)

---

### Post by Old Pink on 2007-04-21
> **s_p_a_r_k_y said:**
> ctrl-alt-X should be able to kill the X server. Also you can shut town computer from the command line by using ctrl-alt-f1 (ctrl alt f7 bring you back to graphical) and logging in then typing in reboot or shutdown (or to restart graphical sudo /etc/init.d/gdm restart)

I knew all of those when it first happen. The computer is frozen and accepts no commands. The ONLY resort is holding of power button until forced/cold shutdown. :(

---

### Post by MonoBrow_063 on 2008-02-10
[FONT="Tahoma"]I'm having the same problem. Everything closes, fullscreen wallpaper left and thats it. Keyboard locked out, won't respond to anything except the power button.

Got to tty2 (Ctrl+Alt+F2) and used sudo reboot. No errors. Tried sudo /etc/init.d/gdm restart and again no probs, only when I use the graphical interface. Leads me to think it's something to do with X possibly. Tried Ctrl+Alt+Backspace and that also freezes.

Any ideas? I'm off with work for a month tomorrow and the missus doesn't like Ubuntu in the slightest. Help!!!![/FONT]

---

