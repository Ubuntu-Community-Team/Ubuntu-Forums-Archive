---
title: "no X11 after update, tty1"
date: 2009-01-01
forum: General Help
---

### Post by arohanui on 2009-01-01
I've just updated from 7.10 to 8.10, and have been having trouble since trying to configure my monitor/GPU (see [http://ubuntuforums.org/showthread.php?t=1026645](http://ubuntuforums.org/showthread.php?t=1026645)).

I switched to safe graphics mode, activiated the nvidia proprietory driver, and then added the data for my VW2226w into xorg.conf.  I restarted, and things were looking okay, except for an NVidia "no screen(s) found" error which meant that X11 used a default resolution (which at least had the correct aspect ratio).

However, when I turned my system on this morning, X11 refused to start up, and I'm dropped straight into tty1 before reaching the login screen.  I don't remember doing anything last night to have changed from a not-working-perfectly-but-usable X11 to a failing X11.

I haven't got as far yet as configuring a network between my two computers, so I can't cut-n-paste from /var/log/syslog, but there is a console-kit-daemon error: WARNING unable to activate console: No such device or address.  

I don't know where to go from here.
Any ideas?
Thanks

---

### Post by dexter on 2009-01-01
If you can login to tty, create a backup of your xorg.conf, remove it and regenerate one using the command "nvidia-xconfig". Afterwards you can restart gnome using "sudo /etc/init.d/gdm restart".

---

### Post by arohanui on 2009-01-01
Weirdness.  

I got stuck in tail, couldn't ^D out, so I hard rebooted, and it XWindows started this time.

Oh well, the above instructions will be very helpful if it happens again.
Thanks so much for your help.

---

