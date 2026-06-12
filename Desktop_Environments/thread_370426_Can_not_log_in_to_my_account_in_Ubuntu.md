---
title: "Can not log in to my account in Ubuntu"
date: 2007-02-25
forum: Desktop Environments
---

### Post by john13th on 2007-02-25
I was trying to install and activate Xgl/Compiz by following this instruction on the site [http://www.tectonic.co.za/view.php?id=916](http://www.tectonic.co.za/view.php?id=916) and there it said that I should input this code in the .Xsession-file:

#!/bin/sh
# Start up Xgl, compiz, and GNOME
# Run Xgl server on :1, on top of normal X
Xgl :1 -fullscreen -ac -accel xv -accel glx:pbuffer &
# Tell subsequent X programs to access the Xgl server at :1
DISPLAY=:1
# Start Compiz window manager
gnome-window-decorator &
compiz gconf decoration wobbly fade minimize cube rotate zoom scale move resize place menu switcher &
# Start GNOME 
exec gnome-session

After I did that I restarted Ubuntu and then I got the message where an error had occured while running the .Xsession-script. This was in the terminal-mode and I couldnt start GNOME. So I erased the whole code I added in the .Xsession-file and while I did manage to start GNOME as usual, I got the error message "Your session only lasted less than 10 seconds" when I logged in on my account. I only could access it by logging into failsafe mode. This is what is was written in the .Xsession-errors-file:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "john"
/etc/gdm/Xsession: Beginning session setup...

How do you fix this? Because otherwise I have no choice but to reinstall Ubuntu thanks to this strange error.

---

