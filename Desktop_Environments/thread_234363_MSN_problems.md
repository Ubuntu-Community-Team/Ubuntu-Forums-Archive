---
title: "MSN problems"
date: 2006-08-11
forum: Desktop Environments
---

### Post by chedabob on 2006-08-11
Well, ill start with GAIM. it works the first time i install ubuntu, but after a reboot, it just loads the buddy list then fails. It just disappears.

Kopete wont run connect (the butterfly logo just stays gray), which i think is cos im running Compiz instead of Gnome.

And AMSN wont run at all. Im using the latest version from their site. It just makes a box on the taskbar, saying "starting amsn" then it just disappears and does nothing. theres no process running.

any ideas what to do? I really want to keep XGL and Compiz.

---

### Post by orasis on 2006-08-11
> **chedabob said:**
> Well, ill start with GAIM. it works the first time i install ubuntu, but after a reboot, it just loads the buddy list then fails. It just disappears.

Kopete wont run connect (the butterfly logo just stays gray), which i think is cos im running Compiz instead of Gnome.

And AMSN wont run at all. Im using the latest version from their site. It just makes a box on the taskbar, saying "starting amsn" then it just disappears and does nothing. theres no process running.

any ideas what to do? I really want to keep XGL and Compiz.


Do not use GAIM for MSN connections, open Synaptic - search for "AMSN" install it and enjoy ;) 

P.S remove the version you downloaded before you install AMSN from Synaptic package manager.

---

### Post by orasis on 2006-08-11
Oh yes and by the way, most of the time when the "offical" AMSN from the site does not work - it is because you are lacking libraries. - So if you are the hacker type, try monitoring it from a shell, and see what it says. 

Or go the easy way, and simply search "AMSN" in Synaptic, which will install the req libs by itself - 123 chat :)

---

### Post by tomtom_in_eire on 2006-08-11
Also, if you are behind a restrictive firewall, make sure aMSN is using the HTTP method. Otherwise, connections will never occur...

---

### Post by fandelau on 2006-08-18
> **chedabob said:**
> 
And AMSN wont run at all. Im using the latest version from their site. It just makes a box on the taskbar, saying "starting amsn" then it just disappears and does nothing. theres no process running.


I'm in the same boat... but I fixed the aMSN not opening with this...

```
sudo ln -s /etc/X11/rgb.txt /usr/share/X11/rgb.txt
```

that will fix it...

My problem is that when I start chatting, the backspace, enter, arrow, etc. keys won't work... instead of backspace to delete the previous char I get a "\b", instead of sending the message with enter I get a "\r", etc... that is the most annoying thing I've ever experienced... 
Please help!

---

