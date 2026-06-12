---
title: "[SOLVED] Error when screenlets start (compiz)"
date: 2007-08-23
forum: Desktop Effects &amp; Customization
---

### Post by master_kernel on 2007-08-23
2 questions. I am using screenlets version 0.0.10-3 from the [http://hendrik.kaju.pri.ee/ubuntu/](http://hendrik.kaju.pri.ee/ubuntu/) repository for feisty. When I open the screenlets manager, I get this error:
> Unable to connect or launch daemon. Some values may be displayed incorrectly.
This problem may have been solved in a french ubuntu forum but I can't read french and google translate didn't work. Also, I cannot install new screenlets because of this error:
> Invalid archive. Archive must contain a directory with the screenlet's name.
I looked in the archive, and the format was valid, but the error still came up. Any help is appreciated.

---

### Post by joco2 on 2007-08-25
Yeah i am getting that same error message, 

the french post is not solved either I got this translation using babel

Hello has all, I installed the new version of screenlet after having removed the old one and with the démmarage of screenlets-manager I have the error message according to which is posted: Unable to connect gold launch daemon. Some been worth may Be displayed incorrectly. Does somebody know or that comes?? I have also another problem with Beryl, I have two icons in the bar of the spots whereas beryl is neither in preferences/sessions nor in config/autostart.

and in the second post i think he is just giving it a bump

As for our problem I am not sure, other than this error it seems to launch fine though when i restart the calender and cpu screenlets don't display

---

### Post by frenchcr on 2007-08-25
master kernel....make sure that you have compiz-fusion running when you start screenlets.

I had the same error, so i closed screenlets, started compiz with compiz --replace, then open screenlets and the error was gone.

---

### Post by jdeslip on 2007-08-29
I am using 0.0.10 on fedora and I have the exact same error.  It seems to occur even if I start screenlets after compiz.  Although it only happens the first time I launch screenlets-manager - after that the error seems to be gone.  Also, the calendar applet doesn't seem to start at login.

---

### Post by lorddeus on 2007-08-30
Active Widget Layer in compiz fusion settings

---

### Post by kholsheimer on 2007-09-01
I had the same problem, I simply removed the **> /dev/null** part in the Main Menu entry. To do this right-click on the Main Menu panel-applet and navigate to the **screenlets** entry (it's under System>Preferences) and double-click to edit it. I simple changed
```
/usr/local/share/screenlets-manager/screenlets-manager.py > /dev/null
``` into ```
/usr/local/share/screenlets-manager/screenlets-manager.py
```I don't really know that much about it, so it might be a stupid method, but it worked for me.

Hope this helps.

---

### Post by shareMenaPeace on 2007-12-22
ty the above method fixed it for me too ... also it want start and deleteting wallpaper changer inside .screenlets fixed it

---

