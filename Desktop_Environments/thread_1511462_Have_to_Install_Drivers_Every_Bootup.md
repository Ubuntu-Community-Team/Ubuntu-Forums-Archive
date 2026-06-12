---
title: "Have to Install Drivers Every Bootup"
date: 2010-06-16
forum: Desktop Environments
---

### Post by Aflack on 2010-06-16
Quite simple. When i start, compiz is turned off, and i have to install drivers.

Then it works no problem.

Happens every boot up.

I have Nvidia Geforce 9400gt. Any suggestions?

Also: My mouse is extremely sensitive, even when i have EVERYTHING turned down. How can i fix this...
If i turn it up the mouse still gets even more sensitive but if i turn it all the way down its still way too sensitive.

---

### Post by Aflack on 2010-06-17
Bump

---

### Post by dabl on 2010-06-17
It's a little hard to know what is behind your problem, but I'll offer some thoughts (since no one else is ...).

1. Driver installation is by "root" or the Super User, but running compiz is a user-space operation.  I wonder if you've inadvertently gotten "sudo" involved in running compiz?

2. I always install the downloaded Nvidia driver from a tty console, and after ```
sudo service kdm stop
```  (gdm for Gnome desktop).  If your /etc/X11/xorg.conf file is working correctly, do not answer "YES" on the step where the Nvidia installer asks if you want a new xorg.conf file written.

Restart the X server with ```
sudo service kdm start
``` (gdm for Gnome).

3. Log in.  Pop open a terminal window, and start compiz with ```
compiz --replace &
```

BTW, since the advent of 10.04 and KDE 4.4 (now 4.5 Beta), I have discontinued running compiz on Kubuntu -- the KDE "Desktop Effects" are close enough for my purposes, and a bit easier on the resources.

Hope this helps.  :)

---

### Post by Aflack on 2010-06-17
> **dabl said:**
> It's a little hard to know what is behind your problem, but I'll offer some thoughts (since no one else is ...).

1. Driver installation is by "root" or the Super User, but running compiz is a user-space operation.  I wonder if you've inadvertently gotten "sudo" involved in running compiz?

2. I always install the downloaded Nvidia driver from a tty console, and after ```
sudo service kdm stop
```  (gdm for Gnome desktop).  If your /etc/X11/xorg.conf file is working correctly, do not answer "YES" on the step where the Nvidia installer asks if you want a new xorg.conf file written.

Restart the X server with ```
sudo service kdm start
``` (gdm for Gnome).

3. Log in.  Pop open a terminal window, and start compiz with ```
compiz --replace &
```

BTW, since the advent of 10.04 and KDE 4.4 (now 4.5 Beta), I have discontinued running compiz on Kubuntu -- the KDE "Desktop Effects" are close enough for my purposes, and a bit easier on the resources.

Hope this helps.  :)
i will try this in a little bit and post back with results. but how do i get to the tty command line thing?

---

