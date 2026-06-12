---
title: "how to install compiz-fusion?"
date: 2008-09-29
forum: Desktop Environments
---

### Post by ieBrazil on 2008-09-29
I have already read sth on the internet on it, but you know I thought it was supposed to be installed as default on Hardy Heron version.

I have been sent to look and set some things on 'desktop settings' on preferences, but there's no desktop settings on that menu.

What do I do in order to get the four environments?

Tnx.



ieBrazil

---

### Post by Kevbert on 2008-09-29
First thing is what display adapter are you using ?  You can get this by going to Applications-Accessories-Terminal and typing in ```
lspci
``` The display adapter is normally the last item on the list.  Compiz will work with most Intel, ATI and Nvidia cards.
If you go to System-Preferences-Advanced Desktop Settings, the manager is there.  If not you need to download CCSM.  Go to Applications-Add/Remove and search for CCSM.  You should now have the Advanced Desktop Settings menu item.

---

### Post by tromort on 2008-09-29
```
sudo aptitude install compizconfig-settings-manager
```
 will install the settings manager if you dont have that yet. you can find it in System > Preferences > Advanced Desktop Effects Settings.

---

### Post by ieBrazil on 2008-09-29
> **Kevbert said:**
> First thing is what display adapter are you using ?  You can get this by going to Applications-Accessories-Terminal and typing in ```
lspci
``` The display adapter is normally the last item on the list.  Compiz will work with most Intel, ATI and Nvidia cards.
If you go to System-Preferences-Advanced Desktop Settings, the manager is there.  If not you need to download CCSM.  Go to Applications-Add/Remove and search for CCSM.  You should now have the Advanced Desktop Settings menu item.

on Synaptic manager, I found this:

- sdcc... and
- simple ccsm... 

what shall I do with it?

On add/remove search thing you told me to do, resulted in 'no applications available'...




OH OH OH WAIT! I have installed these things right up here and ... now I got a simple Compiz Config Settings Manager! 

where should I change for using the cube?

---

