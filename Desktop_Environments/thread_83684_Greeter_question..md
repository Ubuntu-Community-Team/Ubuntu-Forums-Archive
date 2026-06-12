---
title: "Greeter question."
date: 2005-10-29
forum: Desktop Environments
---

### Post by jameswilliams on 2005-10-29
I've been trying for a couple days now to install a updated nvidia driver to support dual-head in X.  I'm having problems reconfiguring my system to not load the greeter at startup and just go to a standard console login so I can startx if I want to after I log in.  How is this done?

Thanx,
James

---

### Post by swerner on 2005-10-29
I don't know if this will help you: [http://www.ubuntuguide.org/#disablenvidialogo](http://www.ubuntuguide.org/#disablenvidialogo)

---

### Post by katu on 2005-10-30
>  to not load the greeter at startup and just go to a standard console login 

If the text console is what you want at startup I think there are two ways to do this: the quick and dirty and nicer but longer.
What you are trying to do is disable the so called login manager. for ubuntu (kubuntu) this is called gdm (kdm). 

*quick and dirty:*
Edit the file **/etc/X11/default-display-manager** and change the name in there to something that doesn't exist on your system (I use kdm so I changed it to /usr/bin/gdm). After restarting the computer you should have a nice console login. 
Note however, that you won't be able to run kdm or gdm at all probably. startx should work fine.

*proper*: 
This is how it should be done properly ;-). Using the graphical configurations and whatnot. Under kubuntu open: 
**->system settings->system services **
under ubuntu look for something similar - it should say services or something related. after opening you should have long list of daemons (services) and a runlevel. Find kdm or gdm and disable start at boot at "run level 5" (this is what the system boots into by default.)

Now for some reason on my machine the config programs are behaving weird under kubuntu. if this is your case  as well, run:
  ```
  sudo serviceconfig  
```
from console. From there it should be ok. 

hope this helps,
cheers,
Katu

---

