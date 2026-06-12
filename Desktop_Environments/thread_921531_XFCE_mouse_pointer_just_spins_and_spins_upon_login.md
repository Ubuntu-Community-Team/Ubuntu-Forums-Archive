---
title: "XFCE: mouse pointer just spins and spins upon login"
date: 2008-09-16
forum: Desktop Environments
---

### Post by gmstalk on 2008-09-16
Hello,

I installed Xubuntu so that I could use XFCE. I usually use regular Ubuntu (gnome) with compiz for the eyecandy. Sometimes I need a more streamlined and less process intensive desktop, thus XFCE. 

My problem is when I chose XFCE and login, I see the decktop, but the mouse pointer endlessly spins and I can do nothing. 

I tried uninstalling, reinstalling, and just stalling with no success (though I am good at stalling). 

Can you help me identify some logs to look at and guide me based on those logs? I would sure appreciate it. 

-Greg

---

### Post by Private_Ops on 2008-09-16
Tried a different mouse?

---

### Post by gmstalk on 2008-09-16
I was unclear. The pointer indicates the system is busy after I have logged in to the XFCE session. I see the only the wallpaper. I can move the pointer fine, so it is not a mouse issue. The system is doing something, but I do not know what. 

I have left it in this state for 9 hours and it never stops. They system just stays busy. No ICONs appear. Right or left clicking does nothing.

---

### Post by mali2297 on 2008-09-17
> **gmstalk said:**
> 
My problem is when I chose XFCE and login, I see the decktop, but the mouse pointer endlessly spins and I can do nothing. 

Have you tried killing the X server (Ctrl+Alt+Backspace) or switching tty (Ctrl+Alt+F[1-6])?

> 
Can you help me identify some logs to look at and guide me based on those logs? I would sure appreciate it. 


Check /var/log/Xorg.0.log and /var/log/Xorg.0.log.old.

---

### Post by gmstalk on 2008-09-17
> **mali2297 said:**
> Have you tried killing the X server (Ctrl+Alt+Backspace) or switching tty (Ctrl+Alt+F[1-6])?

Oh yes, all that works fine. 

> 
Check /var/log/Xorg.0.log and /var/log/Xorg.0.log.old.

Perfect. I will take a look at these files and see what is going on.

---

### Post by mali2297 on 2008-09-18
Another thing that you can try is to go to tty2 (Ctrl+Alt+F2), log in and stop gdm with
```

sudo /etc/init.d/gdm stop

```
Then try to start xfce with
```

startxfce4

```
If it does not work, you might still get some useful error message printed on tty2.

---

