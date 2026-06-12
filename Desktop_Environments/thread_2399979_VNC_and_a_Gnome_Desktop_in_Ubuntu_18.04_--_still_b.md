---
title: "VNC and a Gnome Desktop in Ubuntu 18.04 -- still broken?"
date: 2018-08-31
forum: Desktop Environments
---

### Post by etm2 on 2018-08-31
Alright everyone, I just KNOW someone out there has this working and can help.  I've googled and googled and I'm at my wits end.

Problem: Ever since 14.04, getting a VNC session to serve up a plain old Gnome Desktop is impossible.  The xstartup example files that you see floating around (and I have mine, below) do not work.  

The best I have been able to do is get gnome-panel working, and to launch a terminal from which I can do some work remotely.  However, copy-paste does not work.  There is no background, which is ugly, and the window decoration looks weird/absent (see screenshot). 

The only command in my xstartup that fails is gnome-settings-daemon.  I understand this used to be a single script that is now broken into smaller ones, however, I haven't been able to get "equivalent functionality" out of running them (I may not be trying to run them properly, I don't know).

PLEASE if you have a working xstartup on a vanilly 18.04 Ubuntu install that serves up a nice remote GNOME desktop, I will be forever grateful.

Here is my xstartup file:

```

#!/bin/sh
export XKL_XMODMAP_DISABLE=1

# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
unset DBUS_SESSION_BUS_ADDRESS
# exec /etc/X11/xinit/xinitrc


if [ -z "$SSH_AUTH_SOCK" ]
then
   KILL_AGENT=yes
   eval `ssh-agent -s`
fi
if [ -z "$DBUS_SESSION_BUS_ADDRESS" ]
then
   eval `dbus-launch --exit-with-session --sh-syntax`
fi
gnome-session
if [ "$KILL_AGENT" = "yes" ]
then
   ssh-agent -k
fi

gnome-panel &
gnome-settings-daemon &
metacity &
nautilus &
gnome-terminal &

```

And here is a log from launching the session:

```
31/08/18 21:04:42 Xvnc version TightVNC-1.3.10
31/08/18 21:04:42 Copyright (C) 2000-2009 TightVNC Group
31/08/18 21:04:42 Copyright (C) 1999 AT&T Laboratories Cambridge
31/08/18 21:04:42 All Rights Reserved.
31/08/18 21:04:42 See [http://www.tightvnc.com/](http://www.tightvnc.com/) for information on TightVNC
31/08/18 21:04:42 Desktop name 'X' (syros:1)
31/08/18 21:04:42 Protocol versions supported: 3.3, 3.7, 3.8, 3.7t, 3.8t
31/08/18 21:04:42 Listening for VNC connections on TCP port 5901
Agent pid 14701
unset SSH_AUTH_SOCK;
unset SSH_AGENT_PID;
echo Agent pid 14701 killed;
/home/meyer/.vnc/xstartup: 26: /home/meyer/.vnc/xstartup: gnome-settings-daemon: not found
metacity-Message: 21:04:43.872: could not find XKB extension.

(metacity:14741): metacity-WARNING **: 21:04:43.875: Failed to create MetaCompositorXRender: Missing composite extension required for compositing

** (gnome-panel:14739): WARNING **: 21:04:43.908: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
Nautilus-Share-Message: 21:04:44.518: Called "net usershare info" but it failed: Failed to execute child process &#8220;net&#8221; (No such file or directory)

31/08/18 21:04:46 Got connection from client 127.0.0.1
31/08/18 21:04:46 Using protocol version 3.8
31/08/18 21:04:46 Full-control authentication passed by 127.0.0.1
31/08/18 21:04:46 Pixel format for client 127.0.0.1:
31/08/18 21:04:46   8 bpp, depth 8
31/08/18 21:04:46   true colour: max r 7 g 7 b 3, shift r 0 g 3 b 6
31/08/18 21:04:46 Using tight encoding for client 127.0.0.1
31/08/18 21:04:46 rfbProcessClientNormalMessage: ignoring unknown encoding 16
31/08/18 21:04:46 rfbProcessClientNormalMessage: ignoring unknown encoding 9
31/08/18 21:04:46 rfbProcessClientNormalMessage: ignoring unknown encoding -65527
31/08/18 21:04:46 Using compression level 9 for client 127.0.0.1
31/08/18 21:04:46 Using image quality level 0 for client 127.0.0.1
31/08/18 21:04:46 Enabling X-style cursor updates for client 127.0.0.1
31/08/18 21:04:46 Enabling cursor position updates for client 127.0.0.1
31/08/18 21:04:46 rfbProcessClientNormalMessage: ignoring unknown encoding -131072
31/08/18 21:04:46 rfbProcessClientNormalMessage: ignoring unknown encoding -223
31/08/18 21:04:46 Enabling LastRect protocol extension for client 127.0.0.1
31/08/18 21:04:46 rfbProcessClientNormalMessage: ignoring unknown encoding -131071
31/08/18 21:04:46 rfbProcessClientNormalMessage: ignoring unknown encoding -131070
31/08/18 21:04:46 rfbProcessClientNormalMessage: ignoring unknown encoding -131069
31/08/18 21:04:46 rfbProcessClientNormalMessage: ignoring unknown encoding -309
31/08/18 21:23:58 Client 127.0.0.1 gone
31/08/18 21:23:58 Statistics:
31/08/18 21:23:58   key events received 4382, pointer events 1506
31/08/18 21:23:58   framebuffer updates 2702, rectangles 22892, bytes 4456499
31/08/18 21:23:58     LastRect markers 685, bytes 8220
31/08/18 21:23:58     cursor shape updates 81, bytes 5798
31/08/18 21:23:58     cursor position updates 1, bytes 12
31/08/18 21:23:58     copyRect rectangles 4, bytes 64
31/08/18 21:23:58     tight rectangles 22121, bytes 4442405
31/08/18 21:23:58   raw bytes equivalent 238505326, compression ratio 53.688335

31/08/18 21:24:02 Got connection from client 127.0.0.1
31/08/18 21:24:02 Using protocol version 3.8
31/08/18 21:24:02 Full-control authentication passed by 127.0.0.1
31/08/18 21:24:02 Pixel format for client 127.0.0.1:
31/08/18 21:24:02   8 bpp, depth 8
31/08/18 21:24:02   true colour: max r 7 g 7 b 3, shift r 0 g 3 b 6
31/08/18 21:24:02 Using tight encoding for client 127.0.0.1
31/08/18 21:24:02 rfbProcessClientNormalMessage: ignoring unknown encoding 16
31/08/18 21:24:02 rfbProcessClientNormalMessage: ignoring unknown encoding 9
31/08/18 21:24:02 rfbProcessClientNormalMessage: ignoring unknown encoding -65527
31/08/18 21:24:02 Using compression level 9 for client 127.0.0.1
31/08/18 21:24:02 Using image quality level 0 for client 127.0.0.1
31/08/18 21:24:02 Enabling X-style cursor updates for client 127.0.0.1
31/08/18 21:24:02 Enabling cursor position updates for client 127.0.0.1
31/08/18 21:24:02 rfbProcessClientNormalMessage: ignoring unknown encoding -131072
31/08/18 21:24:02 rfbProcessClientNormalMessage: ignoring unknown encoding -223
31/08/18 21:24:02 Enabling LastRect protocol extension for client 127.0.0.1
31/08/18 21:24:02 rfbProcessClientNormalMessage: ignoring unknown encoding -131071
31/08/18 21:24:02 rfbProcessClientNormalMessage: ignoring unknown encoding -131070
31/08/18 21:24:02 rfbProcessClientNormalMessage: ignoring unknown encoding -131069
31/08/18 21:24:02 rfbProcessClientNormalMessage: ignoring unknown encoding -309
31/08/18 21:24:06 Client 127.0.0.1 gone
31/08/18 21:24:06 Statistics:
31/08/18 21:24:06   key events received 10, pointer events 30
31/08/18 21:24:06   framebuffer updates 15, rectangles 180, bytes 47028
31/08/18 21:24:06     LastRect markers 8, bytes 96
31/08/18 21:24:06     cursor shape updates 6, bytes 418
31/08/18 21:24:06     cursor position updates 1, bytes 12
31/08/18 21:24:06     tight rectangles 165, bytes 46502
31/08/18 21:24:06   raw bytes equivalent 1810106, compression ratio 38.925337

31/08/18 21:24:26 Got connection from client 127.0.0.1
31/08/18 21:24:26 Using protocol version 3.8
31/08/18 21:24:27 Full-control authentication passed by 127.0.0.1
31/08/18 21:24:27 Pixel format for client 127.0.0.1:
31/08/18 21:24:27   8 bpp, depth 8
31/08/18 21:24:27   true colour: max r 7 g 7 b 3, shift r 0 g 3 b 6
31/08/18 21:24:27 Using tight encoding for client 127.0.0.1
31/08/18 21:24:27 rfbProcessClientNormalMessage: ignoring unknown encoding 16
31/08/18 21:24:27 rfbProcessClientNormalMessage: ignoring unknown encoding 9
31/08/18 21:24:27 rfbProcessClientNormalMessage: ignoring unknown encoding -65527
31/08/18 21:24:27 Using compression level 9 for client 127.0.0.1
31/08/18 21:24:27 Using image quality level 0 for client 127.0.0.1
31/08/18 21:24:27 Enabling X-style cursor updates for client 127.0.0.1
31/08/18 21:24:27 Enabling cursor position updates for client 127.0.0.1
31/08/18 21:24:27 rfbProcessClientNormalMessage: ignoring unknown encoding -131072
31/08/18 21:24:27 rfbProcessClientNormalMessage: ignoring unknown encoding -223
31/08/18 21:24:27 Enabling LastRect protocol extension for client 127.0.0.1
31/08/18 21:24:27 rfbProcessClientNormalMessage: ignoring unknown encoding -131071
31/08/18 21:24:27 rfbProcessClientNormalMessage: ignoring unknown encoding -131070
31/08/18 21:24:27 rfbProcessClientNormalMessage: ignoring unknown encoding -131069
31/08/18 21:24:27 rfbProcessClientNormalMessage: ignoring unknown encoding -309


```



Screenshot:


[ATTACH=CONFIG]280931[/ATTACH]

---

### Post by etm2 on 2018-09-01
I want to mention that this xstartup worked PERFECTLY in Ubuntu 14.04.

---

### Post by muktupavels on 2018-09-02
```
#!/bin/sh

export XKL_XMODMAP_DISABLE=1
export XDG_CURRENT_DESKTOP="GNOME-Flashback:GNOME"
export XDG_MENU_PREFIX="gnome-flashback-"

gnome-session --session=gnome-flashback-metacity --disable-acceleration-check &
```

Try that! If does not work then append --debug to gnome-session line and post log file.

gnome-session will try to start full default session (I think) and that will not work as gnome-shell / mutter requires compositing manager or maybe it even does not do that because acceleration-check fails. From log file you probably already know that composite extension is not available...

---

### Post by obbart on 2018-11-21
> **muktupavels said:**
> ```
#!/bin/sh

export XKL_XMODMAP_DISABLE=1
export XDG_CURRENT_DESKTOP="GNOME-Flashback:GNOME"
export XDG_MENU_PREFIX="gnome-flashback-"

gnome-session --session=gnome-flashback-metacity --disable-acceleration-check &
```

Try that! If does not work then append --debug to gnome-session line and post log file.

gnome-session will try to start full default session (I think) and that will not work as gnome-shell / mutter requires compositing manager or maybe it even does not do that because acceleration-check fails. From log file you probably already know that composite extension is not available...

hi, that solution works for me but only if I start vncserver as root, otherwise I obtain only a dotted gray screen with the X pointer. Adding --debug to gnome-session I get the following:

```

Xvnc Free Edition 4.1.1 - built Feb 25 2015 23:02:21Copyright (C) 2002-2005 RealVNC Ltd.
See http://www.realvnc.com for information on VNC.
Underlying X server release 40300000, The XFree86 Project, Inc




Wed Nov 21 16:22:02 2018
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on port 5901
 vncext:      created VNC server for screen 0
error opening security policy file /etc/X11/xserver/SecurityPolicy
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Speedo/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/misc/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/75dpi/, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/100dpi/, removing from list!
Could not init font path element /usr/share/fonts/X11/75dpi/, removing from list!
Could not init font path element /usr/share/fonts/X11/100dpi/, removing from list!
gnome-session-binary[5979]: DEBUG(+): Enabling debugging
gnome-session-binary[5979]: DEBUG(+): hardware acceleration check is disabled
gnome-session-binary[5979]: DEBUG(+): Using systemd for session tracking
gnome-session-binary[5979]: DEBUG(+): GsmManager: setting client store 0x55ceaed39680
gnome-session-binary[5979]: DEBUG(+): GsmXsmpServer: SESSION_MANAGER=local/apollo:@/tmp/.ICE-unix/5979,unix/apollo:/tmp/.ICE-unix/5979
gnome-session-binary[5979]: DEBUG(+): emitting SessionIsActive
gnome-session-binary[5979]: DEBUG(+): fill: *** Getting session 'gnome-session-flashback'
gnome-session-binary[5979]: DEBUG(+): fill: *** Looking if /home/ubuntu/.config/gnome-session/sessions/gnome-session-flashback.session is a valid session file
gnome-session-binary[5979]: DEBUG(+): Cannot use session '/home/ubuntu/.config/gnome-session/sessions/gnome-session-flashback.session': non-existing or invalid file.
gnome-session-binary[5979]: DEBUG(+): fill: *** Looking if /etc/xdg/gnome-session/sessions/gnome-session-flashback.session is a valid session file
gnome-session-binary[5979]: DEBUG(+): Cannot use session '/etc/xdg/gnome-session/sessions/gnome-session-flashback.session': non-existing or invalid file.
gnome-session-binary[5979]: DEBUG(+): fill: *** Looking if /usr/local/share/gnome-session/sessions/gnome-session-flashback.session is a valid session file
gnome-session-binary[5979]: DEBUG(+): Cannot use session '/usr/local/share/gnome-session/sessions/gnome-session-flashback.session': non-existing or invalid file.
gnome-session-binary[5979]: DEBUG(+): fill: *** Looking if /usr/share/gnome-session/sessions/gnome-session-flashback.session is a valid session file
gnome-session-binary[5979]: DEBUG(+): Cannot use session '/usr/share/gnome-session/sessions/gnome-session-flashback.session': non-existing or invalid file.
gnome-session-binary[5979]: DEBUG(+): fill: *** Looking if /var/lib/snapd/desktop/gnome-session/sessions/gnome-session-flashback.session is a valid session file
gnome-session-binary[5979]: DEBUG(+): Cannot use session '/var/lib/snapd/desktop/gnome-session/sessions/gnome-session-flashback.session': non-existing or invalid file.
gnome-session-binary[5979]: CRITICAL: We failed, but the fail whale is dead. Sorry....

```

I checked all these paths and they are empty.. also have no clue of how one of these .session file is supposed to look like.:confused:
any idea on whats is going on?
Thanks in advance

---

