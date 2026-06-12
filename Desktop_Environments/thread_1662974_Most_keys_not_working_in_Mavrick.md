---
title: "Most keys not working in Mavrick"
date: 2011-01-09
forum: Desktop Environments
---

### Post by lannetlinux on 2011-01-09
My setup is Asus EEE701SD running Maverick installed off the Live CD about 6 weeks ago.
Everything worked fine until yesterday when I lost most of the keys, but not Ctrl, Alt, Home symbol, Menu symbol.
Keyboard is physically fine as it works correctly in SystemrecCD and when I boot into a recovery root shell, but not when I am running Xorg under Maverick.
Keyboard layout is default US (I an in Australia).
I tried using Onboard, but even that wouldn't input keystrokes into anything.
I tried going in with VNC and that wouldn't work either.
It seems this might be an Xorg problem, but why would it happen suddenly, seemingly without any provocation;  obviously something has changed, but what...
I have removed and reinstalled xserver--xorg using apt-get in a root shell and have also run dpkg-reconfigure xserver-xorg, but nothing has changed.

Thoughts, Ideas, Solutions?

TIA.

---

### Post by Krytarik on 2011-01-09
Check, if there was a related update: /var/log/apt/history.log

BTW, welcome to the forums! ;-)

---

### Post by lannetlinux on 2011-01-09
[QUOTE=Krytarik;10334140]Check, if there was a related update: /var/log/apt/history.log

:popcorn:

You could be on the money.  I don't recall why I ran this in a shell rather than through update-manager, but I did, and it's about this time that everything went pear shaped:

Start-Date: 2011-01-08  10:10:06
Commandline: apt-get upgrade
Upgrade: evolution-common:i386 (2.30.3-1ubuntu7.1, 2.30.3-1ubuntu7.2)
libapparmor1:i386 (2.5.1-0ubuntu0.10.10.2, 2.5.1-0ubuntu0.10.10.3)
libcupscgi1:i386 (1.4.4-6ubuntu2.2, 1.4.4-6ubuntu2.3)
evolution:i386 (2.30.3-1ubuntu7.1, 2.30.3-1ubuntu7.2)
python-aptdaemon-gtk:i386 (0.31+bzr506-0ubuntu4, 0.31+bzr506-0ubuntu5)
python-aptdaemon:i386 (0.31+bzr506-0ubuntu4, 0.31+bzr506-0ubuntu5)
libapparmor-perl:i386 (2.5.1-0ubuntu0.10.10.2, 2.5.1-0ubuntu0.10.10.3)
ubuntu-sso-client:i386 (1.0.7-0ubuntu1, 1.0.8-0ubuntu1)
libevview3:i386 (2.32.0-0ubuntu1, 2.32.0-0ubuntu1.1)
cups-client:i386 (1.4.4-6ubuntu2.2, 1.4.4-6ubuntu2.3)
evince-common:i386 (2.32.0-0ubuntu1, 2.32.0-0ubuntu1.1)
libcupsmime1:i386 (1.4.4-6ubuntu2.2, 1.4.4-6ubuntu2.3)
libsqlite3-0:i386 (3.7.2-1, 3.7.2-1ubuntu0.1)
cups-ppdc:i386 (1.4.4-6ubuntu2.2, 1.4.4-6ubuntu2.3)
libevolution:i386 (2.30.3-1ubuntu7.1, 2.30.3-1ubuntu7.2)
libcupsppdc1:i386 (1.4.4-6ubuntu2.2, 1.4.4-6ubuntu2.3)
cups-common:i386 (1.4.4-6ubuntu2.2, 1.4.4-6ubuntu2.3)
libcups2:i386 (1.4.4-6ubuntu2.2, 1.4.4-6ubuntu2.3)
ifupdown:i386 (0.6.10ubuntu3, 0.6.10ubuntu3.1)
dpkg:i386 (1.15.8.4ubuntu3, 1.15.8.4ubuntu3.1)
aptdaemon:i386 (0.31+bzr506-0ubuntu4, 0.31+bzr506-0ubuntu5)
cups:i386 (1.4.4-6ubuntu2.2, 1.4.4-6ubuntu2.3)
evince:i386 (2.32.0-0ubuntu1, 2.32.0-0ubuntu1.1)
libevdocument3:i386 (2.32.0-0ubuntu1, 2.32.0-0ubuntu1.1)
libcupsdriver1:i386 (1.4.4-6ubuntu2.2, 1.4.4-6ubuntu2.3)
evolution-plugins:i386 (2.30.3-1ubuntu7.1, 2.30.3-1ubuntu7.2)
cups-bsd:i386 (1.4.4-6ubuntu2.2, 1.4.4-6ubuntu2.3)
libcupsimage2:i386 (1.4.4-6ubuntu2.2, 1.4.4-6ubuntu2.3)
gnome-system-tools:i386 (2.32.0-0ubuntu1, 2.32.0-0ubuntu1.1)
End-Date: 2011-01-08  10:17:14

So, what is the culprit?  It strikes me that dpkg or gnome-system-tools look likely suspects, but what, and what is the fix?

TIA.

---

### Post by Krytarik on 2011-01-09
Like I somewhat expected, there is no package in the list which is likely to have caused this.

BTW, it doesn't matter if you update through a GUI or from the command line.

Can you login to the desktop?

If so, try changing the keyboard layout to another one and then back again, through "System -> Preferences -> Keyboard -> Layouts" (if you're running the Netbook Edition, find the equivalent, or choose "Desktop Edition" at login).

---

### Post by lannetlinux on 2011-01-13
> **Krytarik said:**
> Like I somewhat expected, there is no package in the list which is likely to have caused this.

BTW, it doesn't matter if you update through a GUI or from the command line.

Can you login to the desktop?

If so, try changing the keyboard layout to another one and then back again, through "System -> Preferences -> Keyboard -> Layouts" (if you're running the Netbook Edition, find the equivalent, or choose "Desktop Edition" at login).


I can login OK with gdm - works fine.

I tried a variety of keyboard options, but nothing changed.

---

### Post by Krytarik on 2011-01-14
Try this: 

- logout of your session
- switch to a console, e.g. with Alt+F1, and login
- remove or rename the directory "/home/USER_NAME/.gconf/desktop/gnome/peripherals/keyboard"
- switch back to gdm, with Alt+F7 or Alt+F8, and login again

Good luck!

---

### Post by lannetlinux on 2011-01-14
> **Krytarik said:**
> Try this: 

- logout of your session
- switch to a console, e.g. with Alt+F1, and login
- remove or rename the directory "/home/USER_NAME/.gconf/desktop/gnome/peripherals/keyboard"
- switch back to gdm, with Alt+F7 or Alt+F8, and login again

Good luck!

Tks for persisting with your assistance.

I booted into a root shell and renamed the keyboard directory out of the way and then rebooted into a user X session, but that did not resolve the problem.

When I brought up a terminal session and started giving the keyboard a hard trashing then the occasional key came through onto the screen as if I was beating whatever is causing the blocking.

Instead of logging out back to the gdm login screen, I brought up a guest session, and there I was able to get a normal keyboard response in a terminal session.  In my book that indicates something screwy in a configuration in my user area.  I guess I might have to go hunting for any config files with a change around the time that I did the apt-get upgrade.

BTW, Alt+F1 did not produce a CLI login prompt, but Ctrl+Alt+F1 did.

---

### Post by Krytarik on 2011-01-14
> **lannetlinux said:**
> I guess I might have to go hunting for any config files with a change around the time that I did the apt-get upgrade.
The mentioned directory is where the keyboard preferences of Gnome are stored. Maybe you have other apps which manage keystrokes?
> **lannetlinux said:**
> 
BTW, Alt+F1 did not produce a CLI login prompt, but Ctrl+Alt+F1 did.
Sorry, I seem to repeatedly forget about Ctrl. :roll:

---

### Post by lannetlinux on 2011-01-14
[SOLVED]

In the accessibilty option the "Press and Hold (Slow Keys)" option had got itself set on.

Disable that, and it all works

Duh...

---

