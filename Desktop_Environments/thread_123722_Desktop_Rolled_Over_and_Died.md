---
title: "Desktop Rolled Over and Died"
date: 2006-01-30
forum: Desktop Environments
---

### Post by rhat on 2006-01-30
Hi everyone,
I'm not sure how, but I seem to have broken something in ubuntu, and I could really use your help in diagnosing the problem.

It started when I got a pop-up message saying that my audio demon had crashed. I checked, and sure enough, all of the sounds coming out of my computer were wonked out (like they were being played at twice the regular speed).

Knowing that it had been a while since I last rebooted (and that I'd installed plenty of software since then), I gave my PC a reboot.

Now, everything seemed to go fine untill I tried to log back in; I got a nastygram saying that my session had lasted less than 10 seconds and that something had probably gone wrong (it mentioned something about ICEAuthority files). After trying to log in normally several times to no avail, I switched sessions types to "Gnome failsafe", only to find more of the same.

So, now I'm typing this from the "failsafe X-term" session that *did* let me log in.

I don't know where to start looking to fix this, but I'm open to suggestion. Specifically, I think it would be most helpful if somebody might point me in the direction of a log-file so that I might be able to give a decent bug report.

Thanks,
rhat

---

### Post by duff on 2006-01-30
try clearing out your /tmp directory (including the hidden .ICE-unix directory) and login again

---

### Post by rhat on 2006-01-30
Doing a "cd /tmp; rm -rf *" didn't do anything. However, I did find the ~/.xsession-errors file that my login attempt left, I've appended it below:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -
u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "rhat"
/etc/gdm/Xsession: Beginning session setup...
_IceTransTransNoListen: unable to find transport: tcp
_IceTransmkdir: ERROR: euid != 0,directory /dev/X will not be created.
_IceTransmkdir: ERROR: Cannot create /dev/X
_IceTransPTSOpenServer: mkdir(/dev/X) failed, errno = 13
_IceTransOpen: transport open failed for pts/waffle:
_IceTransMakeAllCOTSServerListeners: failed to open listener for pts
_IceTransISCOpenServer: Protocol is not supported by a ISC connection
_IceTransOpen: transport open failed for isc/waffle:
_IceTransMakeAllCOTSServerListeners: failed to open listener for isc
_IceTransSCOOpenServer: Protocol is not supported by a SCO connection
_IceTransOpen: transport open failed for sco/waffle:
_IceTransMakeAllCOTSServerListeners: failed to open listener for sco

** (gnome-session:9501): WARNING **: Unable to read ICE authority file: /home/rh
at/.ICEauthority

---

### Post by LanceM on 2006-01-31
What worked for me:

gnome fail-safe terminal on login

then type the following:

sudo chown <username>:<usergroup> .ICEauthority

so for me it would be
sudo chown lance:lance .ICEauthority

then type exit and login to your regular desktop.

Lance

---

### Post by th2 on 2006-01-31
If you have problems with the command line, and you have the same problem next time, use Blackbox for your session (temporarily), then right click, choose x-term, then type:

```
sudo nautilus
```

Enter your password and then use nautilus to navigate to the .ICEauthority and right click this file, choose properties, and change permissions to where any user on the machine (i.e. you) can read and write to this file.

---

### Post by rhat on 2006-01-31
Thanks alot that seems to have fixed the problem--even the sound is back to normal (although that's probably unrelated).

---

