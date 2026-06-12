---
title: "Maybe has crashed Compiz?"
date: 2012-07-17
forum: Desktop Environments
---

### Post by acutbal on 2012-07-17
Hello!!
Today I've updated (via update manager) some packages of Gnome Classic, and after that when I exited from my session Unity 3D and Gnome Classic didn't work anymore. But Unity 2D and Gnome Shell run fine.

First of all I thought that Ati drivers crashed so I uninstalled but nothing changed. Now I think that perhaps Compiz has crashed. What do you think?

Thanks!!

---

### Post by Frogs Hair on 2012-07-17
I think that makes sense because Classic and Unity use Compiz and the other sessions don't. You could try to reset Compiz.
1. log into Ubuntu 
2. Use Ctrl + Alt + F1 to enter TTY 
3. enter user name and password.
4. run the following commands per Ask Ubuntu.```
sudo gconftool --recursive-unset /apps/compiz-1
``````
sudo gconftool --recursive-unset /apps/compizconfig-1
```
5.wait until any process in tty comlpetes.
6.Re-enter the desktop environment. (Ctrl + Alt + F7)

If nothing has changed restart and log into Ubuntu. If that fails repeat the steps and use the following single command instead of the Compiz restart commands.```
unity --reset
```

---

### Post by acutbal on 2012-07-18
Hi!!

1.000.000 Thanks!! Solved, your solution worked!!

The guilty was Unity, a simple "unity --reset" and all returned to normal.

First of all I've tried the first option but nothing changed so I've passed to the second step. After some error messages the TTY get stuck in the same command line for a 20 minutes or more, then I rebooted the laptop and, voilà, logged in my Ubuntu 3D session without major problem. 

So, thanks again!!!

PD: Taking advantage of the occasion, I apologize for it, but I have a question, my laptop has a switcheable graphic card, and Ati Mobility Radeon HD 4000 series + Ati Mobility Radeon HD 5000 series. 
Well, the point is that AMD with its grand, good and great customer support has decided to not support anymore HD 4000 series in the next release of the propietary drivers, the 12.6, and now I don't know what to do because the HD 5000 series are supported. 
What could happen with the HD 4000  if I update my gpu driver to 12.6?

Thanks for your help!!!

---

### Post by Frogs Hair on 2012-07-18
You are welcome ! Glad it worked .

---

