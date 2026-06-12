---
title: "Xubuntu fluxbox autologin problem (need to turn it off)"
date: 2006-07-20
forum: Desktop Environments
---

### Post by penquin on 2006-07-20
I am using xubuntu on my laptop and I had to install fluxbox so it might be faster.  I changed it from xfce to fluxbox, but stupid me I put it as default and when it came up no menu and now I can't get it back to xfce because I have the autologin.

---

### Post by The Noble on 2006-07-20
> **penquin said:**
> I am using xubuntu on my laptop and I had to install fluxbox so it might be faster.  I changed it from xfce to fluxbox, but stupid me I put it as default and when it came up no menu and now I can't get it back to xfce because I have the autologin.

Seems like you got stuck, but no worries ;) . To get back to the login screen, start Xubuntu in safe mode (from grub), and once you get the terminal, type 
```

xdm

``` 
(I think this is the login manager for Xfce)
This will start up the Login manager. There you are! :D 

If that did not work, 
```

$ sudo apt-get install gdm
$ gdm

``` 

This installs the Gnome gui login manager. Once you get back to Xfce, uninstall gdm. Hopefully this doesn't mess with the Xfce Login GUI. :-? 

Good luck

---

### Post by ubuntu_demon on 2006-07-20
> **penquin said:**
> I am using xubuntu on my laptop and I had to install fluxbox so it might be faster.  I changed it from xfce to fluxbox, but stupid me I put it as default and when it came up no menu and now I can't get it back to xfce because I have the autologin.

How did you configure the autologin ? 

If you are still using gdm then it might be the case that you just need to click on sessions and select a xfce4 session (instead of fluxbox).

The default window manager for xubuntu is xfwm4 and the default login manager is gdm.

You can install gdm by :
$sudo apt-get install gdm

You can setup gdm (inside a graphical environment) by :
$sudo /usr/sbin/gdmsetup

Another thing to try is :

Try logging out of the graphical environment and try startxfce4 :

```

$/usr/bin/startxfce4

```

---

### Post by ofek on 2006-07-20
Posting right now from my fluxbox / xfce dual wm box =P.
I'm willing to help if I can.

---

### Post by penquin on 2006-07-20
thanks guys I feel like such a schmuck

---

### Post by penquin on 2006-07-20
okay I tryed all of the suggestions and my luck is bad.  does anyone know how to get the menu for fluxbox.  if I switch it to icewm will that work?

---

### Post by penquin on 2006-07-20
Thank you everyone for the ideas.  In recovery mode I downloaded kdm and used that to get to xfce and made it default.

---

