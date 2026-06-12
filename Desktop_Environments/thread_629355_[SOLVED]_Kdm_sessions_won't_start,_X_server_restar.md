---
title: "[SOLVED] Kdm sessions won't start, X server restarted"
date: 2007-12-02
forum: Desktop Environments
---

### Post by Oversteer on 2007-12-02
Hello everyone,

I have a problem with my Gutsy Kubuntu on amd64. 
From some days ago, I'can't start any session from the login manager (KDM)

The problem is that Kdm starts and prompts the login screen, once the login starts with correct user and pass, seems that X server restarts and kdm reappers.
Xorg.Log doesn't reports any errors, 

in kdm.log:

 The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
Xlib:  extension "XInputExtension" missing on display ":0.0".
Failed to get list of devices
Xlib:  extension "XInputExtension" missing on display ":0.0".
Failed to get list of devices

But i don't think is the matter.

I tried to do dpkg-reconfigure  for kdm and kdebase, but nothing to do.
Installed Window maker for try another type of session, also nothing to do.

So, If i login from console as root,  kill kdm and do "startx" i can get my kde session correctly.
I have also  vnc4 server installed that worked well, but now is impossible to log-in in Kde or any other session.
I' don't know what happend, i just remember that i've installed windows fonts, was connected with vnc from a winwows remote machine, then the windows screensaver started and vnc connection was broken, and i can't relogin because a message from vnc tells me "Server already in use", then i rebooted the machine but i can't login now (also locally in xserver 0)!!!

Could anyone help me? Are somewhere any login logs that can be analyzed?

Thanks in advance

---

### Post by Oversteer on 2007-12-05
Ok, solved

I made a mistake while installing a package from a tar.gz, then the read permission on /usr and the underlyning directories was changed and only root could read and execute (as well only root could get a kdm session)

Restoring the right permission on the directory /usr  (not recursivly!!) worked well

Bye!

---

