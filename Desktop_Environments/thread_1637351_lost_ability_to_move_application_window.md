---
title: "lost ability to move application window"
date: 2010-12-04
forum: Desktop Environments
---

### Post by telescopic on 2010-12-04
I use Xubunt 10.04, today when login, i found:

1)I lost ability to move application window. eg, The firefox window is stuck and anchored at the upper left corner. I can still resize by dragging the lower right corner. I notice the upper right corner resize tab disappears.

If open another application, it is again anchored at upper left corner and cannot be moved.

2)under Settings>Xfce Setting Manager> Window Manager, all the icons are gone. Same inside Window ManagerTweaks.

I used "xfce4-panel" in terminal, it doesn't help.

Thank you

---

### Post by 3Miro on 2010-12-04
Sounds like the window manager broke down. Try
```
xfwm4 --replace
```

You can run that either from a terminal or from Alt + F2.

---

### Post by telescopic on 2010-12-04
Thank you. That simple line solves the problem. 
And, if I boost my computer and it just starts with a command shell prompte, how to call up the gnome window?

By the way, how do you know that, I used ubuntu for more than 1 year. Every time I have a problem, I have to google if someone else has similar problem and solution.(kind of tired of it) It is a passive learning process. How can I become more active in knowing more linux? Start to learn the Bash script?

Thanks

---

### Post by 3Miro on 2010-12-04
I have been an XFCE user for some time now and I have noticed this behavior when I try to play with compiz. Sometimes xfwm4 (which is the window manager) doesn't start properly and with that command you have that fixed.

If you boot in command line only, then you can start the graphical environment with:
```
 startx 
```
There is also
```
 gdm start 
```
or 
```
 sudo gdm start
```

---

### Post by telescopic on 2010-12-04
I just discover the right-mouse-click still won't produce the context menu. How to fix it?

---

### Post by 3Miro on 2010-12-04
Where is it that you are right-clicking? If you cannot right-click on the desktop, you can open a Taskmanager and kill xfdesktop (or alternatively start is from Alt + F2).

---

### Post by telescopic on 2010-12-04
See this is another command I don't know. Thanks a lot. 

From the terminal, i type:  
>xfdesktop

The context menu pop up after clicking the right mouse button pointing at desktop.

I look at  Application>settings>xfce 4 setting manager>session and startup

choose session tab, then those command you told me are now there. Choose save session.

I don't know why this morning those command became missing. 

Thanks, will mark solved

---

