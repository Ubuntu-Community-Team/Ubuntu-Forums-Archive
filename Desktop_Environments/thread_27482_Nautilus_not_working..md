---
title: "Nautilus not working."
date: 2005-04-16
forum: Desktop Environments
---

### Post by bobmitch on 2005-04-16
Gnome starts, metacity works (I can launch windowed apps) - but nautilus does run at all.

It passes it's self check mode from the command line - but I have no desktop background, no icons, and cannot browse files/folders using nautilus.

How do I start tracing the cause of the problem?

---

### Post by p!=f on 2005-04-16
If you create another user account, does (s)he experience the same problem?
Please run 
```

dpkg -l | grep -v ^ii

```
and post the output here.
Also, take a look at the ~/.xsession-errors file.

---

### Post by bobmitch on 2005-04-16
[QUOTE=p!=f]If you create another user account, does (s)he experience the same problem?
Please run 
```

dpkg -l | grep -v ^ii

```
and post the output here.
Also, take a look at the ~/.xsession-errors file.[/QUOTE]



.xsession-errors:

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "mitch"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/mitch:/tmp/.ICE-unix/7112
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
Gnome-Message: gnome_execute_async_with_env_fds: returning -1

** (gnome-cups-icon:7230): WARNING **: failed request with status 1030

** (gnome-cups-icon:7230): WARNING **: failed request with status 1030

** (gnome-cups-icon:7230): WARNING **: failed request with status 1030

** (gnome-cups-icon:7230): WARNING **: failed request with status 1030

** (gnome-cups-icon:7230): WARNING **: failed request with status 1030

** (gnome-cups-icon:7230): WARNING **: failed request with status 1030

** (gnome-cups-icon:7230): WARNING **: failed request with status 1030

** (gnome-cups-icon:7230): WARNING **: failed request with status 1030
:
``` 

Results for dpkg -l:

```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
rc  gdesklets      0.33.1-1ubuntu an advanced architecture for desktop applets
rc  libc6-i686     2.3.2.ds1-20ub GNU C Library: Shared libraries [i686 optimi
rc  libe           0.17.0_pre10-0 Enlightenment library.
rc  libedje0       0.5.0.003-0cvs Graphical layout and animation library
rc  libengrave0    0.1.0-0cvs2005 Enlightenment edje EDC parsing library API
rc  libesmart0     0.9.0.002-0cvs The Esmart Prototype Library
rc  libetox0       0.9.0.002-0cvs Evas-based text layout library
rc  libewl0        0.0.4.002-0cvs The Enlightened Widget Library (EWL)
rc  libflash0      0.4.11-2       GPL Flash (SWF) Library - shared library
rc  libxfce4mcs-cl 4.0.6-1        Client library for Xfce4 configure interface
rc  libxfce4mcs-ma 4.0.6-1        Manager library for Xfce4 configure interfac
rc  monkey-bubble  0.3.2-1        The GNOME bust'a'move clone
rc  totem-gstreame 1.0-0ubuntu2   A simple media player for the Gnome desktop
rc  xfce4          4.0.5-1        Installs XFce4 core and scripts to set it up
rc  xfce4-session  0.1.3+20031213 XFce4 Session Manager
rc  xfdesktop4     4.0.6-1        Provides desktop background and root menu
```

Will test another user now as well.  [EDIT]  The problem is only for my current (main) user.  Thanks for any help. :)

---

### Post by p!=f on 2005-04-16
[QUOTE=bobmitch]
Will test another user now as well.  [EDIT]  The problem is only for my current (main) user.  Thanks for any help. :)[/QUOTE]
Try this...
CTRL+ALT+F1
```

sudo /etc/init.d/gdm stop
mv ~/.nautilus ~/.nautilus.old
sudo /etc/init.d/gdm start

```
Any difference? If not
```

sudo /etc/init.d/gdm stop
mv ~/.nautilus ~/.nautilus.old
mv ~/.gnome2 ~/.gnome2.old
sudo /etc/init.d/gdm start

```
To recreate your GNOME profile.

---

### Post by bobmitch on 2005-04-16
The problem doesn`t appear to be reproduceable.

4 reboots - no config changes - and on the final one, nautilus starts up just fine.

 :?

---

### Post by Dracontopes on 2005-04-16
Sometimes I got the same problem.

No deskstop background (just the brown color), no right-mouse menu on desktop and loggin of or shutting down takes 5 minutes before the system actually reboots. 

Now, when I do

```

killall nautilus

```

everything returns to normal. Weird! It only happens sometimes.

(Oh and BTW, I am using the Breezy updates...)

---

### Post by bobmitch on 2005-04-16
[QUOTE=Dracontopes]Sometimes I got the same problem.

No deskstop background (just the brown color), no right-mouse menu on desktop and loggin of or shutting down takes 5 minutes before the system actually reboots. 

Now, when I do

```

killall nautilus

```

everything returns to normal. Weird! It only happens sometimes.

(Oh and BTW, I am using the Breezy updates...)[/QUOTE]

That works for me too.  Didn`t even think to do a ps -ef to see if it was already running. :D

(On Hoary here btw)

---

### Post by h2g2 on 2007-12-23
> **Dracontopes said:**
> Sometimes I got the same problem.

No deskstop background (just the brown color), no right-mouse menu on desktop and loggin of or shutting down takes 5 minutes before the system actually reboots. 

Now, when I do

```

killall nautilus

```

everything returns to normal. Weird! It only happens sometimes.

(Oh and BTW, I am using the Breezy updates...)

I had the same problem. This fixed it just fine. Thanks

---

