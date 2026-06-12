---
title: "help!"
date: 2007-09-11
forum: Desktop Effects &amp; Customization
---

### Post by ebrammer252 on 2007-09-11
I installed a new login theme and I hit CTRL+ALT+Backspace to restart the x window app, when I did it just went to a black screen with the busy cursor.  I restarted and same thing.  I'm a n00b to Ubuntu, how can I fix this and just revert back to my old settings and what did I do wrong?

Thanks,

Eric

---

### Post by Rupertronco on 2007-09-11
Going to need some more info. What theme did you install and from where? Also, are you using KDM or GDM (ubuntu or kubuntu)? 

What was the exact procedure you used to install this theme? You're probably going to have to fix this from the command line.

---

### Post by ebrammer252 on 2007-09-11
I'm using Ubuntu, 7.04 Fiesty Fawn to be exact, I used this theme : [http://art.gnome.org/themes/gdm_greeter/1201](http://art.gnome.org/themes/gdm_greeter/1201)
I downloaded the compressed file saved it in my Home folder.  Went into the login manager and installed it, I then selected the radio button next to it and closed the login manager.  I used CTRL+ALT+Backspace to restart X window and bleh, I'm here now (in XP...dual boot)

---

### Post by hyperair on 2007-09-11
You can try this:
1. Ctrl+Alt+F1
2. Log into the terminal
3. Turn off GDM:
```

sudo /etc/init.d/gdm stop

```
4. Create and edit your .xinitrc file:
```
nano ~/.xinitrc
```
5. type:
```

#!/bin/sh
exec gnome-session

```
6. Type Ctrl+X and then Y to exit.
7. Make .xinitrc executable:
```
chmod +x .xinitrc
```
8. Type "xinit" without the quotes to start a login session. If it doesn't take you there immediately, press Ctrl+Alt+F7.
9. Do your repair work (change the theme in your login manager to something that works), then log out.
10. Head back to the terminal
11. Turn on GDM:
```

sudo /etc/init.d/gdm start

```

---

### Post by ebrammer252 on 2007-09-11
Well I got to step 9 and I hit a roadblock.  When I try to go and switch my logon theme back to the default I get an error.  Upon trying to open the login window manager it says "Failed to run /usr/sbin/gdmsetup as user root.  Unable to copy the user's xauthorization file."

what am I missing here?

-Eric

---

