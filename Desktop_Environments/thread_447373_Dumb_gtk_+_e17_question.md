---
title: "Dumb gtk + e17 question?"
date: 2007-05-17
forum: Desktop Environments
---

### Post by darkenedday on 2007-05-17
Okay, I absolutely love E17 it's fast, flashy, and intuitive, I've managed to configure just about everything the way I want it except one small annoying issue that I can't seem to figure out myself,

I changed my theme to milky, and it changes the window decorations and the colours inside the window in enlightenment native apps to the corresponding white colour, however for gtk based apps (such as GAIM or Firefox)I still end up with this ugly annoying greyish theme that clashes with the window decorations and reminds me of archaic windows, I;ve looked through all the setting (I think) and I can't seem to find anywhere to change this?

help please

thanks!

---

### Post by Co.Sinecure on 2007-05-24
There should be an application you can use called (something like) gtk-switch-theme that will change the theme used by gtk apps only. I'm yet to experiment with it to get a theme to match my e17 theme,,

---

### Post by darkenedday on 2007-05-26
thanks for the tip I'll take a look into that :-)

---

### Post by Co.Sinecure on 2007-05-27
darkenedday, the actual program is gtk-theme-switch2

---

### Post by RedSquirrel on 2007-05-27
Actually, it's just **gtk-theme-switch**. ;)

---

### Post by hanzomon4 on 2007-06-01
Just add "gnome-settings-daemon" to the start up applications.

---

### Post by loell on 2007-06-01
oh thanks , i was wondering about this too. :)

but a follow up question, will this slow down e17's start-up ?

---

### Post by hanzomon4 on 2007-06-01
I haven't noticed any slowdown on startup, but results may vary....

---

### Post by darkenedday on 2007-06-02
Thanks Alot guys,  will isntall this app as soon as i can replace my main pc's power supply

---

### Post by RedSquirrel on 2007-06-03
Just to clarify what I wrote earlier, the *package* name is gtk-theme-switch.

```
 sudo apt-get install gtk-theme-switch
```Then you can run it in a terminal with

```
 switch2
```to change GTK+ 2.0 themes, and

```
switch
```to change GTK+ 1.2 themes. You may also see "gtk-theme-switch" and "gtk2-theme-switch" in your menu.

gnome-settings-daemon may be another possibility, but only if you have GNOME installed; not everyone does. :D

---

### Post by hyperair on 2007-09-18
And how dyou get it to start up with E17?

---

### Post by the yawner on 2007-09-18
I got it done with a *.gtkrc-2.0* file containing something like this:
> gtk-theme-name = "gtk theme name"

---

### Post by hyperair on 2007-09-18
Ah ok, thanks. How do you get a custom application to start up in E17? As in a custom application, something not already found in the menu.

---

### Post by the yawner on 2007-09-18
I may not be correct but I believe it goes this way. First you need to create a *.desktop* file for that application. But you don't have to manually create one on E17. Click...

- Menu > Configuration > Configuration Panel
- On category Applications, click New Application
- Fill up the parameters: Name, Executable, and Comment. Add an icon too. But don't click apply yet.
- Click Advanced and under Categories put *Application* and any other existing category which the app falls under. Just separate it with a *;* (semi-colon).
Example: 
App: Firefox
Categories: Applications;Network

Note: You may reference the Application Categories on the control panel for the full category list.

- Click Apply

After you have done this your new application will now be added on whatever category you indicated as mentioned above. And you can now add it to the IBar apps, Restart Apps, and Startup apps. Another note is that if you have the checkbox *Show in menus* checked, then the new app should now appear on the matching category on your menu.

====
Actually, I have tried first what I wrote just now and I can confirm this working. I 'created' an entry for application gcalc-tool (a calculator) with no icon (to separate it to the existing .desktop file) and under Category: *Applications;Network*
After clicking the apply button, the app is now selectable under category Network if I want it added on the IBar. It also now appears on the menu under category Internet :D
(Using E17 installed over Xubuntu btw.)

Please try it out yourself. Cheers.

---

### Post by hyperair on 2007-09-18
Ah thanks. What about disk mounter applets? Are there any that I can use to mount and unmount my external storage devices?

---

### Post by amr2205 on 2007-10-02
> **hanzomon4 said:**
> Just add "gnome-settings-daemon" to the start up applications.

JeJe... I have forgotten the name, thanks! ;)

---

