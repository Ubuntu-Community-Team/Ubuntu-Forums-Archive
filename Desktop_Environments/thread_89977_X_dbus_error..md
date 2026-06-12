---
title: "X dbus error."
date: 2005-11-13
forum: Desktop Environments
---

### Post by Fredric on 2005-11-13
I seem to be having a problem logging into my  new installation of Hoary..  Gdm tries to come up, the screen flickers for a while, and then it goes to the non-graphical login with error messages about not being able to locate fonts..

I'm not sure what the fonts have to do with it, but I logged into my user account, and tried to run startx.  The screen flickered, and I got the same error.  I looked in the .xsessions_error file, and saw this:

> 
Failed to start message bus: Failed to read directory "/usr/share/dbus-1/services": Permission denied
EOF in dbus-launch reading address from bus daemon


I can log in as root, and using startx get everything up and going.  I did a chmod 755 on the /usr/share/dbus-1/services directory, but the problem remains the same.  There is nothing in that directory as well, that might have something to do with it.

Any suggestions?

-Fredric

---

### Post by Ampersand on 2005-11-14
To start with, make sure everything installed properly by running
```
sudo apt-get install ubuntu-desktop
```

---

### Post by Fredric on 2005-11-15
I was able to restart it a few times before it screwed up.  When I run that it tells me...

> 
Reading package lists... Done
Building dependency tree... Done
ubuntu-desktop is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Which I guess means everything is there.

Any thoughts?

-Fredric

---

