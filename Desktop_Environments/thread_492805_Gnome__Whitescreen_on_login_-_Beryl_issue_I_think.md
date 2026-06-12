---
title: "Gnome  Whitescreen on login - Beryl issue I think"
date: 2007-07-05
forum: Desktop Environments
---

### Post by whistlerspa on 2007-07-05
XServer crashed recently back to 640X480 so i reconfigured it via sudo dpkg-reconfigure. 

OK so far but when I then tried to reenable beryl it now white screens. All i can do then is ctrl+alt+backspace back to re-login. Luckily I do have KDE desktop environment as well so can still use the box. 

But my preference is to Gnome. I tried reinstalling all Beryl and Compiz packages but this failed to make any difference. 

In KDE if I start Beryl manager I get the same white screen but not on login as in Gnome.
It happened after today's updates (could just be coincidental). I have an ATI Radeon 9600 which I understand is known to be problematical but it's never done this before.


Has anyone had this problem and found a way to fix please?

---

### Post by spoilerhead on 2007-07-05
look for "whitescreen of death" here:
[http://forum.beryl-project.org/](http://forum.beryl-project.org/)
[http://forums.opencompositing.org/](http://forums.opencompositing.org/)

---

### Post by whistlerspa on 2007-07-10
Can't find anything relevant on either link. Tried totally removing beryl. No good

CAN ANYONE PLEASE PLEASE PLEASE TELL ME HOWE TO GET RID OF THIS F***ING WHITE SCREEN!!!!!!!!!!!!!!!!!!!!!!1

---

### Post by whistlerspa on 2007-07-10
Perhaps I need to rant more often when i have a Gnome issue. it's miraculously restored itself - perhaps reinstalling beryl or using the command i found on another thread helped. 

Let's see if it lasts. Will steer clear of Beryl from now on on this computer though

---

### Post by Lesterchakyn on 2007-07-13
In some versions of Beryl this was fixed with the "copy" option under rendering path (advanced beryl options) in the beryl-manager

Or start beryl with the "--use-copy" option

This seems to be been fixed in newer releases :)

---

### Post by castoroil97 on 2007-07-15
driver issue, most likely

make sure your driver is installed and you are able to have direct rendering

---

