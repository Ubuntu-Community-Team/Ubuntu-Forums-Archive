---
title: "Restricted nvidia drivers have broken xserver"
date: 2009-05-27
forum: Desktop Environments
---

### Post by madsporkmurderer on 2009-05-27
On a clean jaunty install I installed the nvidia 180 restricted drivers. After a restart of gdm, x will not restart; it is giving the error 'no screens found'. I have searched and found that this seems to be a common problem, but cannot find a way to remove these drivers to get it back to how it was. Can this be done?

Thanks,
Mike

---

### Post by andrea000 on 2009-05-28
hello,

have you have went to system-> administration-> hardware drivers
and changed them there it should have switched it back.You can
also try [envyNG]("http://www.albertomilone.com/envyngfaq.html") from synaptic that should tell what driver is
recommended for the video card.

---

### Post by madsporkmurderer on 2009-05-28
Unfortunately I can't get X started to get to that menu, I need a way to get to it from the command line.

I managed to 'fix' it with a fresh install, I then used git on the whole of /etc, tried installing the other driver that the restricted drivers tool reccomended and got the same issue.

I used aptitude purge nvidia-glx-173 followed by a git reset --hard on etc and still got the same error. Where do these drivers hide, and why does a reset of /etc/X11/xorg.conf not switch back to using the old drivers?

Thanks,
Mike

---

### Post by andrea000 on 2009-05-28
To reset your X config to its default installed state, run

sudo dpkg-reconfigure -p high xserver-xorg

---

### Post by acepukas on 2009-05-30
Hi There,

I'm also having issues with X after installing the nvidia drivers. Can't boot to GUI, but I have access to the terminal as root via recovery mode (Ubuntu 9.04)

I have tried the command:

sudo dpkg-reconfigure -p high xserver-xorg

and /etc/X11/xorg.conf was reset and a backup was made.

I diff'd the back up with newly created xorg.conf and they were identical.

Here is the contents of my xorg.conf after running the dpkg-reconfigure command.

--- File comments header removed ---

Section "Device"
    Identifier    "Configured Video Device"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
EndSection

Also, and maybe this was a bad idea but I also uninstalled the nvidia-glx package in the hopes that the system woule default to the "default" drivers. No such luck.

I tried using the xfix utility from the recovery mode menu. No luck with that either.

I am about to just reinstall the system fresh but I would prefer not to. Has anyone had similar issues?

---

### Post by asmoore82 on 2009-05-30
you could try forcing the free `nv` driver:

```
sudo nano /etc/X11/xorg.conf
```
and edit it so that it looks like this:
```
#...

Section "Device"
	Identifier	"Configured Video Device"
[COLOR="Blue"]	Driver		"nv"[/COLOR]
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection
```

then restart gdm ```
sudo /etc/init.d/gdm restart
```

---

### Post by krazyd on 2009-05-31
You need to run```
sudo nvidia-xconfig
```It should work on the xorg.conf you got from ```
sudo dpkg-reconfigure -p high xserver-xorg
```

---

