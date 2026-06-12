---
title: "Compiz Fusion Help!"
date: 2011-07-16
forum: Desktop Environments
---

### Post by mclizardman on 2011-07-16
I installed Coompiz Fusion, and tried to get the cube effect through the CompizConfig Settings Manager, and tried to enable the effect. I may have done something wrong, but now (Im in gnome), All the status bars have disappeared. The only way I was able to get into FireFox was to log into Ubuntu in No Effects made. So, can someone help me? Thanks! I am not the best with Ubuntu, I am a Windows user at heart, so I will appreciate the help greatly.

---

### Post by Frogs Hair on 2011-07-16
Some information about your Ubuntu version and computer hardware may be a good place to start .

---

### Post by mclizardman on 2011-07-16
> **Frogs Hair said:**
> Some information about your Ubuntu version and computer hardware may be a good place to start .

Okay.  Ubuntu 11.04
AMD Phenom II X2 555
4 gb of DDR2 Ram
Radeon HD 5750 graphics

---

### Post by Frogs Hair on 2011-07-16
For Unity !

If you can run a command using Alt+F2  , use this command .```
unity --reset
```

If you are unable to run a command using Alt+F2 see post 2 @ the link .
[http://ubuntuforums.org/showthread.php?p=11050449#post11050449](http://ubuntuforums.org/showthread.php?p=11050449#post11050449)

If want to enable the cube in unity see the link . [http://amazingubuntucube.blogspot.com/](http://amazingubuntucube.blogspot.com/)

---

### Post by mclizardman on 2011-07-16
> **Frogs Hair said:**
> For Unity !

If you can run a command using Alt+F2  , use this command .```
unity --reset
```If you are unable to run a command using Alt+F2 see post 2 @ the link .
[http://ubuntuforums.org/showthread.php?p=11050449#post11050449](http://ubuntuforums.org/showthread.php?p=11050449#post11050449)

If want to enable the cube in unity see the link . [http://amazingubuntucube.blogspot.com/](http://amazingubuntucube.blogspot.com/)

Thanks! but I perfer and typically use Gnome. Any help there?

---

### Post by Frogs Hair on 2011-07-16
> **mclizardman said:**
> Thanks! but I perfer and typically use Gnome. Any help there?

Try the command to reset Compiz to defaults , again using Alt + F2. You can also enter the recovery console by selecting it from the session list below the greeter box at the login screen and run the command from there if Alt + F2 doesn't work . Restart after entering the command and login to Classic Gnome . I would do a search for information for setting up the cube in Classic Gnome . I was not aware there were any special steps .```
gconftool-2 --recursive-unset /apps/compiz
```

---

### Post by rickytikki on 2011-07-16
> **mclizardman said:**
> Thanks! but I perfer and typically use Gnome. Any help there?

Before you log in there should be a ubuntu classic option which will take you to the original ubuntu gnome task bar etc. from there compiz should work normally

---

### Post by Frogs Hair on 2011-07-16
> **rickytikki said:**
> Before you log in there should be a ubuntu classic option which will take you to the original ubuntu gnome task bar etc. from there compiz should work normally

He was using Classic when this happened .

---

### Post by mclizardman on 2011-07-16
Okay, sorry for the late reply. I got the cube animation running in Unity, but while trying to set it up in Gnome I somehow got rid of the ability to move windows around and got rid of the close icons on the top left of the window bar. IN fact, the bar is completely gone. Is there a simple way to fix this or do I have to reset Gnome like I did in Unity?

---

