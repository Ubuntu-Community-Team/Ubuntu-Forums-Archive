---
title: "Not able to loggon..."
date: 2006-01-03
forum: Desktop Environments
---

### Post by lucidite on 2006-01-03
I think there might be something wrong with my computer. For the last few times, whenever I'd do something in sudo, I'd get an error message saying that I was using another number then what I was assigned (I guess for permissions or whatever...)
Then tonight, I rebooted and got this message:

/etc/gdm/Presession/Default: Registring your session with wtmp and utmp
/etc/gdm/Presession/Default: running /usr/bin/X11sessreg -a -w /var/logwtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "caro"
/etc/gmp/Xsession: Beginning session setup...
grep: /etc/gconf/1/path: No suce file or directory
grep: /etc/gconf/1/path: No suce file or directory
/etc/X11/Xsession.d/20desktop-profiles_activateDesktopProfiles: line 138 /usr/lib/GNUstep/System/Library/Makefiles/user_home: No such file or directory
/etc/X11/Xsession.d/20desktop-profiles_activateDesktopProfiles: line 157 /usr/lib/GNUstep/System/Library/Makefiles/user_home: No such file or directory
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid !=0.directory /dev/X will not be created.
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir (/dev/X) failed, erno = 13
_IceTransOpen: transport open failed for pts/vishnu:
_IceTransMakeAllCOTSServerListeners: failed to open listener for ISC
_IceTransSCOOpenServer: Protocol is not supported by SCO connection
_IceTransOpen: transport open failed for sco/vishnu:
_IceTransMakeALLCOTSServerListeners: failed to open listener for sco

** (gnome-session: 7834): WARNING ** : Unable to read ICE Authority file: /home/caro/.ICEauthority


(end)

Any idea how I can fix this?

---

### Post by amohanty on 2006-01-03
Log into the recovery console and post the output of:
> ls -l .ICEauthority

---

### Post by lucidite on 2006-01-03
The response is:
-rw-------  1 root root 732 206-01-03 19:07 .ICEauthority

---

### Post by ATAQ on 2006-01-03
I tried sudo chmod a+wr /home/yourusernamehere/.ICEauthority

And It allowed me to login.

---

### Post by lucidite on 2006-01-03
Typed that in my command line, nothing happened.

---

### Post by amohanty on 2006-01-04
Try this on the command line:

> sudo chown your_username:your_username .ICEauthority

Basically in **your** account you should be the owner of the file, not root. The permissions are ok, its the owner thats the problem.

HTH
AM

---

### Post by lucidite on 2006-01-04
This seems to work so far!

If I may ask, however, 
a) do you have any idea what happened? Or what *might* have happened for me to have this problem?
b) what did that last command do that it fixed things?

I'd like to know what I did wrong/right that way if possible I'll avoid that in the future. 

Oh, and THANKS!

---

### Post by amohanty on 2006-01-04
> a) do you have any idea what happened? Or what might have happened for me to have this problem?

There are too many possible ways to mess this up but most probably you did something as sudo that changed the ownership of the file. One of the most likely reasons is that that you login as yourself into recovery console and then do something like starting the xserver/gnome via sudo.

> b) what did that last command do that it fixed things?

chown changes the ownership of the file to username:groupname.

HTH

---

### Post by lucidite on 2006-01-05
Thank you again for your help!

And if this happens again, I'll know what to do!

---

