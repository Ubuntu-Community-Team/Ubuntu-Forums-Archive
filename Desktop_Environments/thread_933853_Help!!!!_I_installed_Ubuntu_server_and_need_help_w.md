---
title: "Help!!!! I installed Ubuntu server and need help with GUI"
date: 2008-09-29
forum: Desktop Environments
---

### Post by EarleRamage on 2008-09-29
I installed Ubuntu server along with FVWM-Crystal and VNC. I need to know how to configure Ubuntu server to automatically start my window manager at login. That is how to start FVWM-Crystal automatically after logging in with out me having to type startx at the command prompt.

I have researched but most recommend to install Ubunbtu desktop however this choice is unacceptable.

---

### Post by wizard10000 on 2008-09-30
> **EarleRamage said:**
> I installed Ubuntu server along with FVWM-Crystal and VNC. I need to know how to configure Ubuntu server to automatically start my window manager at login. That is how to start FVWM-Crystal automatically after logging in with out me having to type startx at the command prompt.

I have researched but most recommend to install Ubunbtu desktop however this choice is unacceptable.

Installing gdm should get you where you want to be.

---

### Post by prshah on 2008-09-30
> **EarleRamage said:**
> I installed Ubuntu server along with FVWM-Crystal and VNC. I need to know how to configure Ubuntu server to automatically start my window manager at login. That is how to start FVWM-Crystal automatically after logging in 

Edit / create a file "~/.xinitrc" and place in it the command to start the Window Manager you want. I don't know what you will use for FVWM-Crystal, but here's an example for KDE:```

# Start KDE as default WinMgr
exec startkde
```

Replace the part after exec with the command you currently use to start FVWM-Crystal.

If you're looking to start X automatically as well, you need to add a script to the /etc/init.d/ directory. Call it whatever you want (something simple), place it in /etc/init.d/ using sudo and/or gksudo, and then run update-rc.d to start the script. Example```

sudo nano /etc/init.d/startgui.sh
# /bin/bash
exec startx
# press Ctrl+X to quit, and save when prompted
sudo chmod u+x /etc/init.d/startgui.sh
sudo update-rc.d startgui.sh defaults

```

If "startx" doesn't work for you, use "xinit".

You will still need the .xinitrc file.

---

### Post by EarleRamage on 2008-10-02
Thanks, I will try this l8tr :-). I must say I am finding Ubuntu to be a trip, considering I didn't have quite as much challenges when I was using Mandriva. But for what I am currently doing I need a lean mean serving machine. 
Thanks a lot for the support.

---

### Post by EarleRamage on 2008-10-02
Ok Ok Ok so I couldn't wait. I took the advice I got and I installed xdm after some tweaking I got my FVWM-Crystal to strat just like I want it. Thanks again. Didn't know it was so simple. I was afraid I would ave had to do some script work in initrd or rc which I was trying to avoid and actually did :-)

---

