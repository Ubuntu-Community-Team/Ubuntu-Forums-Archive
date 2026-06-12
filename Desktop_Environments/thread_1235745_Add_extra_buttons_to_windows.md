---
title: "Add extra buttons to windows"
date: 2009-08-09
forum: Desktop Environments
---

### Post by Richardarkless on 2009-08-09
Hey is it possible to add extra window buttons to the title bar, I would want to be able to add a roll up button so it rolls the window contents to the title bar like in xubuntu. Im sure it is possible as xfce is pretty much a older version of gnome.

I am using ubuntu 9.04 x64

Thanks
Richard

also if it is possible what other buttons can I add apart from the default ones and roll up

oh and how would one set a cursor, I installed one under appearances and customised it to use the cursor but it only shows in firefox and no where else

---

### Post by mcduck on 2009-08-09
Gnome's default window manager Metacity doesn't support any extra buttons (although it does support window shading, usually activated by double-clicking the window's titlebar).

If you use Compiz as your window manager, Emerald does support some extra buttons for windows. You can configure them with the Emerald Theme Manager.

What comes to your cursor problem, programs usually need to be restarted before they start using the new cursor. So you'll pretty much have to log out and back again after changing the cursor to make it work correctly for everything.

(and no, XFCE is not an "older version of Gnome", the only thing it has in common with Gnome is that both use GTK as their toolkit)

---

### Post by Richardarkless on 2009-08-09
> **mcduck said:**
> Gnome's default window manager Metacity doesn't support any extra buttons (although it does support window shading, usually activated by double-clicking the window's titlebar).

If you use Compiz as your window manager, Emerald does support some extra buttons for windows. You can configure them with the Emerald Theme Manager.

oh right, ok, I never liked emerald and seemed buggy the last time I used it where one moment it would show the emeralt themed title bar then randomly it would crash (back in 8.10) gonna have to try it again see if it has improved

> What comes to your cursor problem, programs usually need to be restarted before they start using the new cursor. So you'll pretty much have to log out and back again after changing the cursor to make it work correctly for everything.

(and no, XFCE is not an "older version of Gnome", the only thing it has in common with Gnome is that both use GTK as their toolkit)

lol I never actually tried logging off and logging back in, thanks that worked

oh right thanks for correcting my error

Thanks 
Richard

---

### Post by gjoellee on 2009-08-09
You can run XFCE's window manager inside GNOME. That will give you those buttons. Just install XFWM4 (XFCE's window manager):
```
sudo apt-get install xfwm4
```

When it is installed press Alt + F2 then run ```
xfwm4
```.

If the window borders does not change please run ```
xfwm4
``` in the terminal and post the output.

Then just make xfwm4 start on startup. Go to System->Preferences->Sessions and click on "Add". Then name it what you want, add the whatever comment you want but at the command section add: ```
xfwm4
```.

---

