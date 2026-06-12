---
title: "task bar disappeared!"
date: 2009-04-10
forum: Desktop Environments
---

### Post by simon dew on 2009-04-10
Booted up my Asus Eee this morning and my task bar has disappeared completely. I wonder if someone can tell me how to restore it. I accessed firefox by right clicking and creating a launcher but this is going to get tiresome. I can't imagine why the task bar has gone apart from perhaps a bug in the latest security update?

Cheers

Simon

---

### Post by hictio on 2009-04-10
You mean a Panel?
Do you still have one on screen? If so, do a right click on an empty place of it, and from the pop-up menu, select "New Panel".
And then, on another right click on the new Panel, and set it to the correct position you want it, and then add stuff to it :D
The Task List applet it is called "Window List".

EDIT:
Disregard, didn't notice you are running Xubuntu, that is, XFCE.

---

### Post by simon dew on 2009-04-11
No, I don't seem to have any panel at all. I have managed to configure it so I have my menus on the right click now but I would like to get it back to the way it was before. All help appreciated!

Cheers
Simon

---

### Post by roccity1 on 2009-04-11
you can try adding xfce4-panel in your startup and sessions.right click and go to settings manager and add xfce4-panel in the startup and sessions there.

---

### Post by siyabonga on 2009-04-13
Thanks for the advice. I had the same problem recently (also running Xubuntu 8.04), which I solved by adding an autostarted application in Applications -> Settings -> Settings Manager -> Autostarted Apps, with the code "xfce4-panel &". Might not be the best solution, but it works. 

Any idea what causes the panels to disappear? I've been screwing around with my wireless settings recently, so it may have something to do with that. Another thing: at the same time that the panels disappeared, I started getting a Firefox window popping up every time I rebooted. Haven't figured out how to stop that yet.




[SIZE="1"]Just lost my forum-virginity...[/SIZE]

---

### Post by djbushido on 2009-04-13
Tinkering with wireless has nothing to do with panels disappearing. Nor does a firefox window appearing. That was probably because firefox wasn't shut down right, or at all.
No idea why this is happening, look and see if you can re-create the problem.

---

### Post by jedistorm on 2009-04-15
{[QUOTE=siyabonga;7066314]Thanks for the advice. I had the same problem recently (also running Xubuntu 8.04), which I solved by adding an autostarted application in Applications -> Settings -> Settings Manager -> Autostarted Apps, with the code "xfce4-panel &". Might not be the best solution, but it works.] 

I followed your steps and it works for me.

Thank you

---

### Post by ahbart on 2009-04-15
Just wondering, did you recently try the netbook remix switcher?

---

### Post by siyabonga on 2009-04-15
> **djbushido said:**
> Tinkering with wireless has nothing to do with panels disappearing. Nor does a firefox window appearing. That was probably because firefox wasn't shut down right, or at all.
No idea why this is happening, look and see if you can re-create the problem.

Firefox kept starting up every time I rebooted until I followed the advice on this thread:
[http://ubuntuforums.org/showthread.php?t=1102643&highlight=firefox+startup]("http://ubuntuforums.org/showthread.php?t=1102643&highlight=firefox+startup")

Incidentally, this also gives a better way of ensuring that the panels are there on startup: Type 
```
xfce4-panel &
```
in the command line, which should bring back the panels if they've gone missing. Then restart, making sure that you tick the "save session for future logins" box. Untick this the next time you shut-down / restart.

---

