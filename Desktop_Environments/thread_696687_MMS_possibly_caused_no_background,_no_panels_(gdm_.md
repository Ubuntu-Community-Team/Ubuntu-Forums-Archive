---
title: "MMS possibly caused no background, no panels (gdm fails)"
date: 2008-02-14
forum: Desktop Environments
---

### Post by avdzm on 2008-02-14
Hey all,

I just installed MMS,

and I decided to restart my laptop and when i logged in,
my background, my icons n my panel disappeared!!! :cry:

the only thing that loads is avant-window-navigator (awn) :D.

luckily i have webmin installed n i can run commands in there n browse my files via firefox n remote :D.

I have tried so many things n nothing brings back my desktop :cry:.

i have tried;
restarting gdm, nothing
restarting emerald, nothing
restarting compiz, nothing,
un-installing mms, nothing,
i've tried running /usr/bin/gnome-session-properties, the msg i get is "cannot open display"

the funny thing is that my screen saver runs, n i have firefox dock on awn n it runs.
I can also rotate the cube (ctrl+alt n move mouse), zoom (winkey + scroll)

at the moment i can still access my files via samba so i'm backing up incase i do something stupid...

any help will be greatly appreciated. 	:smile:

thanks
avdzm

---

### Post by Crooksey on 2008-02-14
Mms?

---

### Post by avdzm on 2008-02-14
> **Crooksey said:**
> Mms?

It's a linux media center
[http://mymediasystem.org/](http://mymediasystem.org/)

---

### Post by avdzm on 2008-02-14
Here is the log file in /var/log/gdm

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.3)
Current Operating System: Linux avdzm-laptop 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686
Build Date: 18 January 2008
	Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu Feb 14 16:55:28 2008
(==) Using config file: "/etc/X11/xorg.conf"
(II) Module already built-in
(II) Module already built-in
(II) Module already built-in
Atom 4, CARD32 4, unsigned long 4
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Invalid argument
Synaptics DeviceInit called
SynapticsCtrl called.
Synaptics DeviceOn called
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
ProcXCloseDevice to close or not ?
ProcXCloseDevice to close or not ?
ProcXCloseDevice to close or not ?
ProcXCloseDevice to close or not ?
SetClientVersion: 0 9
SetGrabKeysState - disabled
SetGrabKeysState - enabled
SetGrabKeysState - disabled

I have no idea what's wacom! 
Can someone tell me what's this?

thanks

---

### Post by Crooksey on 2008-02-14
Wacom make drawing tablets.

Do you have a wacom entry in xorg.conf?

```

cat /etc/X11/xorg.conf | grep "wacom"
```

---

### Post by avdzm on 2008-02-14
> **Crooksey said:**
> Wacom make drawing tablets.

Do you have a wacom entry in xorg.conf?

```

cat /etc/X11/xorg.conf | grep "wacom"
```

This is the reply
Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"
	Driver		"wacom"
	Option		"Device"	"/dev/input/wacom"

so i guess it's there,
i have also replaced the xorg.conf with the last working xorg.conf.

---

### Post by Crooksey on 2008-02-14
```

cp /etc/X11/xorg.conf /etc/X11/xorg.conf.b #this makes a backup
sudo gedit /etc/X11/xorg.conf

```

Now remove the input device sections for wacom devices.

---

### Post by avdzm on 2008-02-14
:confused:........
Now there's nothing on the screen (after login),
not even the awn,

oh well

once the backup processes is done, 
i'll restart the computer and see,

don't worry i can still access my files via samba & webmin,
Thank fully i installed samba & webmin!!!

the funny thing is the screen saver still comes :)

---

### Post by Crooksey on 2008-02-14
well you can use vim if you like, wont need X for that.

---

### Post by avdzm on 2008-02-14
i'm sorry, why would i use vim?
Isn't vim a cool text editor???

My guess is that u might have miss understood what i meant by backup process,
i'm backing up my personnel files to a ext hdd, just so that my files they r safe...

thanks though

---

### Post by Crooksey on 2008-02-14
Yes, but if X has crashed you can still use runlevel 3, to edit files.

---

### Post by avdzm on 2008-02-14
ah ok, i'll keep that in mind
thanks

---

### Post by avdzm on 2008-02-20
Hey all,
well nothing worked,

so i reinstalled ubuntu,
However i think it had something to do with metacity.
cause i kept on getting errors about not able to **Display**
when i tried executing something.

anyhow thanks for all your help.

---

