---
title: "Different Desktop Sessions"
date: 2013-05-20
forum: Desktop Environments
---

### Post by davey486 on 2013-05-20
My request may or may not even be possible, but here goes.

I have ubuntu installed and have alot of extras. I want to be able to have another login, say XBMC, for xbmc, to have a "clean" login with anything else. I want each login to be able to go to their respective desktop managers without have to switch them in the login sessions menu.

---

### Post by Frogs Hair on 2013-05-20
I have seen this question asked before and as far as I know log-in can't be bypassed. In my case I have Xfce, the Gnome Shell, and Unity . The problem is they are separate sessions and use different window managers though the sessions may share some applications .
 
Unity - Compiz

XFCE- XFWM4
 
Gnome Shell- Mutter

---

### Post by davey486 on 2013-05-20
What I'm meaning is I want to be able to log in as me "david" put my password in and have the computer start up my desktop with conky compiz and all my icons, and when I want to login to watch my htpc, login as "xbmc" put my password in and have it automatically swiched to a more stripped down version because I won't be needing conky or compiz or any other resources that might take away from the XBMC software.

---

### Post by Frogs Hair on 2013-05-20
> [COLOR=#000000] I want each login to be able to go to their respective desktop managers without have to switch them in the login sessions menu.[/COLOR]

This reads like you want to bypass the login screen to change sessions and as far as I know it is not possible. When I experimented with XBMC it had a stand alone session which uses the resources required to run it.

Edit: I just installed the standalone session again, but log out and in are still required.   
 
```
sudo apt-get install xbmc-standalone
```

---

