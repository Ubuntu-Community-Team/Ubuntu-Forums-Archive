---
title: "Oh YAY, XServer refuses to start"
date: 2009-06-18
forum: General Help
---

### Post by Kaymeerah on 2009-06-18
```

kaymeerah@Tarri-XII:~$ sudo startx
xauth:  error in locking authority file /tmp/.gdm4WSJVU
xauth:  error in locking authority file /tmp/.gdm4WSJVU
xauth:  error in locking authority file /tmp/.gdm4WSJVU
xauth:  error in locking authority file /tmp/.gdm4WSJVU
_XSERVTransSocketUNIXCreateListener: ...SocketCreateListener() failed
_XSERVTransMakeAllCOTSServerListeners: server already running

Fatal server error:
Cannot establish any listening sockets - Make sure an X server isn't already running

Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
xinit:  Server error.
xauth:  error in locking authority file /tmp/.gdm4WSJVU
```

and Nvidia GLX says

```
Fail to query the GLX server vendor.
```

compiz says

```

kaymeerah@Tarri-XII:~$ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

```

any ideas? this is all the information i got

now ive tried reinstalling X server, restoring original conf file, reinstalling nvidia drivers... what else can i do? running 9.04 Jaunty

EDIT: i think i worked out a fix, ill update

---

### Post by Kaymeerah on 2009-06-18
nevermind, now it wont load the NVidia drivers at boot, ill give u logs soon

EDIT: Fixed the issue, close the thread please

---

### Post by t4thfavor on 2009-06-18
Glad you let everyone know what fixed the problem... 

If you have a problem please let the rest of the community know when it gets fixed. Otherwise there will just be a bunch of problems, and no solutions.

Thanks,

---

### Post by ericab on 2009-06-18
i agree, maybe you could fill us in ?

---

### Post by Psychoscorpic on 2009-06-29
Um - care to share? You'll be helping quite a few.
My X-Server suddenly stopped yesterday - tried to boot, but can't get to log-on screen.
Tried Recovery Mode's "Try to Repair Display Problems" (or whatever it says) to no avail.

---
Never mind.
I've mostly* fixed it by uninstalling xserver.

```
sudo aptitude remove xserver-xorg
```
Saying Y to its squealing, followed by:
```
sudo aptitude install xserver-xorg
```

Also tried the following "remove"/"install" options, without success before this:
```
sudo aptitude remove xorg
sudo aptitude install xorg
sudo aptitude remove gdm
sudo aptitude remove xterm
sudo aptitude remove x-window-system-core
```

As an aside, closer examination of the corrupt display revealed that it was crushing the entire screen display into the top 1cm of the screen. (Noticed the menu from Recovery Mode was still active, but tiny, up there after manually attempting to start GDM)

If somebody knows a less destructive repair command than reinstalling xserver-xorg, please let us know here for future.

*Mostly?
Uninstalling xserver-xorg took out 189Mb, including all dependencies.
Reinstalling it only replaced 15Mb - so all manner of things need to be reinstalled separately (e.g. the Shutdown button on the panel is gone, as are my ATI proprietry drivers)

---

### Post by Kaymeerah on 2009-08-09
sorry had some RL troubles, im officially back on forums

and okay ill fill u in, DONT FORGET TO DOWNLOAD UR GRAPHICS CARD DRIVERS BEFORE THIS, jump into a GUI free environment (CTRL + ALT + F1-F6), type ```
sudo /etc/init.d/gdm stop
``` (if u use gnome, honestly i dont know about KDE), completely remove xserver and vid drivers with ```
sudo apt-get remove {VIDEO DRIVERS}
``` or ```
sudo apt-get remove xserver-xorg && dependencies
``` (if it complains about && dependencies, just use ```
sudo apt-get remove xserver-xorg
```, not only apt-get install --reinstall like i did, then install them again in netroot recovery console like this ```
apt-get install xserver-xorg
``` ```
sh {driver install path here}
``` as installing tty1-tty6 obviously did not work, reboot.. thats what i did.. worked very well

and yet again im sorry for such a late reply

---

