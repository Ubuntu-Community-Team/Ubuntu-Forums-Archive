---
title: "no gui when I start up"
date: 2010-03-17
forum: Desktop Environments
---

### Post by engine on 2010-03-17
Finished installing 9.10 on a brand-new hard drive, used the machine happily for a couple of days ... and now something I've never experienced before =8-}

Start-up runs as expected till "ubuntu" centre screen with light-effect from above, then I get a black screen. But wait, there's more: on the black portion, all that shows up is the "activity" cursor, but top left there's a terminal session correctly displaying my shell prompt.

On advice, I've tried
```
rm ~/.xinitrc
``` - didn't even have an /xinitrc to delete
```
sudo init 5
``` - did nothing
```
sudo dpkg-reconfigure xserver-xorg
``` and ```
sudo dpkg-reconfigure gdm
``` - did nothing
```
startx
``` - "server is already active for display0"

As I've not created any important files since the install, I suppose I could just try a repair from the installation CD? but it would be good to know what's actually gone wrong.

N

---

### Post by keforex on 2010-03-17
What is the video card? Can you post your xorg.conf?

---

### Post by engine on 2010-03-18
Give me a clue: how do I interrogate the system about the video card, from a command-line?
> >locate xorgconfig
>

---

### Post by keforex on 2010-03-21
Boot from the live CD, open a terminal, type sudo nautilus, navigate to \etc\X11, locate xorg.conf, right click and choose open or open with and use gedit. Copy and paste the contents here.

---

### Post by engine on 2010-03-22
> **keforex said:**
> Boot from the live CD, open a terminal, type sudo nautilus, navigate to \etc\X11, locate xorg.conf, right click and choose open or open with and use gedit. Copy and paste the contents here.

> sudo nautilus

```
(nautilus:3545): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-gdu extension

** (nautilus:3545): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:3545): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:3545): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.
```

Irrelevant, but hardly encouraging!

> navigate to \etc\X11, locate xorg.conf

No such animal:

```
ubuntu@ubuntu:~$ ls /etc/X11
app-defaults
cursors
default-display-manager
fonts
rgb.txt
X
xinit
xkb
Xresources
Xsession
Xsession.d
Xsession.options
XvMCConfig
Xwrapper.config

```

---

### Post by keforex on 2010-03-23
Are you sure you navigated to /etc/X11 ? This folder should be the one inside of your hard drive, not the one in the live CD. The errors you saw when loading up nautilus in root mode are ok, just ignore.

If you installed ubuntu correctly and you are being dropped to the shell prompt, log in with your name and password (if you're not being logged in automatically) and type sartx at the shell prompt to see if the graphic interface loads up.

If that's the case you're golden and you can forget the live CD and just repeat the commands I gave on the previous post to investigate xorg.conf

From there we'll see what the next steps can be. I am guessing the problem is not even in the xorg.conf file - it could be that you have to remove the "ro   quiet splash" line argument that is inside the grub.cfg file that resides inside /boot/grub - in order to edit this file you have to change its permissions to read and write through nautilus in root mode. Right click->Properties->Permissions. Once changed, open it up with gedit and just chop off that "ro  quiet splash" - save and reboot. It should take you to the graphic interface, even though the boot process is now in verbose mode.

---

### Post by engine on 2010-03-24
Thanks for the patient explanation! I'll try again later; though I'm beginning to suspect the root of the problem could be a hardware glitch and failure to mount a partition on the HD. I'll make that a separate thread to avoid confusion ...

---

### Post by engine on 2010-04-01
So ... what have I discovered today?

a) no, there is no xorg-conf in /etc/X11 on the hard drive in question

b) startx fails with the following messages:

```
_XSERVTransSocketUNIXCreateListener: ... SocketCreateListener() failed
_XSERVTransMakeAllCOTSServerListener: server already running
Fatal server error: cannot establish any listening sockets - Make sure an X server isn't already running

```

c) /var/log/log.0.x reports the following:

```
(WW) xf86Close Console KDSETMODE failed: Bad file descriptor
(WW) xf86Close Console VT_GETMODE failed: Bad file descriptor
(WW) xf86Close Console VT_GETSTATE failed: Bad file descriptor

```

Does this bring us any closer to enlightenment? <g>

---

