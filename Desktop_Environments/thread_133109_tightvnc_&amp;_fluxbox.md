---
title: "tightvnc &amp; fluxbox"
date: 2006-02-19
forum: Desktop Environments
---

### Post by promet on 2006-02-19
Heya,

I am trying to nail down my tightvnc configuration. I had first tried using gnome-session as my vnc window manager, but running a second instance of gdm seemed to wreak havoc on my original instance on display :0 . So I decided to try and run fluxbox instead.

The server can be reached and logged into and the base fluxbox screen comes up with it's simple menu. The xterm entry (all I am after really at this point, as I can launch necessary apps from there while i fool with menu-conf stuff),  however will not launch a window.

I need help tweaking my fluxbox conf to get it operable. There are some errors reported in my xvnc log as follows:

" 19/02/06 12:25:55 Xvnc version 3.3.tight1.2.9
19/02/06 12:25:55 Copyright (C) 1999 AT&T Laboratories Cambridge.
19/02/06 12:25:55 Copyright (C) 2000-2002 Constantin Kaplinsky.
19/02/06 12:25:55 All Rights Reserved.
19/02/06 12:25:55 See [http://www.uk.research.att.com/vnc](http://www.uk.research.att.com/vnc) for information on VNC
19/02/06 12:25:55 See [http://www.tightvnc.com](http://www.tightvnc.com) for TightVNC-specific information
19/02/06 12:25:55 Desktop name 'X' (Pliars:1)
19/02/06 12:25:55 Protocol version supported 3.3
19/02/06 12:25:55 Listening for VNC connections on TCP port 5901
Warning: Failed to open file(/usr/share/fluxbox/nls/en_US/fluxbox.cat)
for translation, using default messages.
Failed to read: session.tabs
Setting default value
Failed to read: session.ignoreBorder
Setting default value
Failed to read: session.forcePseudoTransparency
Setting default value
Failed to read: session.numLayers
Setting default value
Failed to read: session.updateDelayTime
Setting default value
Failed to read: session.tabPadding
Setting default value
Failed to read: session.focusTabMinWidth
Setting default value
Failed to read: session.slitlistFile
Setting default value
Failed to read: session.groupFile
Setting default value
Failed to read: session.appsFile
Setting default value
Failed to read: session.tabsAttachArea
Setting default value
Failed to read: session.useMod1
Setting default value
apps file failure
Failed to read: session.screen0.imageDither
Setting default value
Failed to read: session.screen0.opaqueMove
Setting default value
Failed to read: session.screen0.sloppywindowgrouping
Setting default value
Failed to read: session.screen0.workspacewarping
Setting default value
Failed to read: session.screen0.desktopwheeling "


I am assuming these "~/fluxbox.cat" and "Failed to read: ~" errors are the culprit at this point, but would appreciate any help you guys could offer.

:-k 

Thanks,
promet

---

### Post by promet on 2006-02-19
So,

After some tweaking around, I uninstalled tightvnc and installed the "vino" package, and used the Ubuntu "System -> Remote Desktop" to setup remote access. Now, this kind of disturbs my whole "fluxbox/efficiency" thing, but the vino solution seems not to screw with Gnome Ubuntu, and appears to be reliable (at least from another Ubuntu box on my LAN).

I don't know though, if this would still be the case if I were to make Fluxbox my default Window Manager from login (though I suppose I should try this). So any progress on the previous post is very welcome. Just thought I'd point out this workaround for anyone having VNC Problems...

P

---

### Post by bupkes on 2006-10-25
I found this exact same problem using fluxbox/xdm on dapper server install .. but I am using nomachine's NXserver.  I can't seem to find the solution but I have the same symptom (no xterm) and same set of errors.

---

