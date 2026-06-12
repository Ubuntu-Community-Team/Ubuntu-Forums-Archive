---
title: "Cannot loggin just background picture and wait mouse pointer..."
date: 2013-08-08
forum: Desktop Environments
---

### Post by mtmigs on 2013-08-08
My daughter's ubuntu 10.04 computer stopping logging in to her gnome account. Anyone else can still login. It is just her account that fails. It just brings up the background picture and displays the wait mouse pointer. The mouse pointer moves but nothing else happens.

I looked in syslog and found the X startup section. After the startup there is a Gtk warning about "widget not within a Gtkwindow". Then there are another Gtk error but I do not think these are the problem.

Then I found python gets a segfault. Logging in as a different user I found two python tasks run. One is for /usr/share/system-config-printer/applet.py and the other is for /usr/share/ibus/ui/gtk/mail.py. But since the files are not user specific I cannot see why they would segfault for one user and not another.
 
Then pulseaudio starts and trys to start a second time but the second start fails.

Then nautilus gets a segfault in "libc-2.11.1.so".

Then all the applets get segfaults in that same library.

Then nautilus gets more segfault errors in that library or in "libgio-2.0.s0.0.2400.1". It seems to just run away with those two errors; because syslog also has __ratelimit: ?? callbacks suppressed lines interspersed with the nautilus errors. It keeps getting those errors until I kill the X process.

That is with her account. Every other account logs in just fine.

I also noticed metacity is not running for her account.

---

### Post by SurfaceUnits on 2013-08-12
Probably easier to create a temp account, copy her stuff to temp account, delete her user account, then recreate it.

---

### Post by mtmigs on 2013-08-14
I ended up moving everything out of her directory. Then I moved folders in and out of her directory until I found the problem directory, "/home/userx/.local/share/mime". Every time I put that directory back into place the login locks up with the spinning wait mouse pointer.

---

