---
title: "um... gdm not loading?!"
date: 2006-10-04
forum: Desktop Environments
---

### Post by Llewxam on 2006-10-04
while trying to watch a dvd on totem, ubuntu actually froze. i restarted x (ctrl alt backspace) and logged in once more to find that nothing will load. i only get a black screen and nothing else. i kept trying to reboot, tried to fix xserver-config only to find that the package is not found. i'm close to just formatting and reinstalling everything BUT i got too many files and things that i can't possibly lose. i need some big help here anyone please. 
](*,) :confused:

---

### Post by Llewxam on 2006-10-04
anyone? please? ...freaking out here >.<' dunno how to fix this.

---

### Post by Llewxam on 2006-10-04
tried to reconfigure xserver-xorg... nothing.
i'm not getting any error messages
i'm not getting any help either... i can't lose my thesis help please! ](*,)

---

### Post by kerry_s on 2006-10-04
Do you get the login screen? What file system are you using? When you say you kept trying to reboot, did you reboot or it won't reboot? Your not really giving any info, press the rest button and look for any errors when starting. Try editing the bootline and add 1 to it to start without gui than type startx and note the errors if any.

---

### Post by Dinerty on 2006-10-04
Do you have a backup of xorg.conf?

---

### Post by Llewxam on 2006-10-04
> **kerry_s said:**
> Do you get the login screen? What file system are you using? When you say you kept trying to reboot, did you reboot or it won't reboot? Your not really giving any info, press the rest button and look for any errors when starting. Try editing the bootline and add 1 to it to start without gui than type startx and note the errors if any.

yes i get the login screen. yes i rebooted but after the login screen it all goes black.

---

### Post by Llewxam on 2006-10-04
aha.... got something here. after booting up and changing to verbose in the login screen i typed in startx and this is what i get:

xauth: creating new authority file /home/<username>/.serverauth.4770
xauth: /home/<username>/.Xauthority not writable, changes will be ignored
xauth: error in locking authority file /home/<username>/.Xauthority

Fatal server error:
Server is already active for display 0
If this server is no longer running, remove /tmp/.X0-lock and start again.

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified 

giving up.
xinit: unable to connect to X server
xinit: No such process (errno 3): Server errror
xauth: error in locking authority file /home/<username>/.Xauthority

---

### Post by Llewxam on 2006-10-04
i give up. i'll try and transfer the files into my pen drive and after wards will format.

---

