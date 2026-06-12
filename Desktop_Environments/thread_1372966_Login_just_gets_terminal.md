---
title: "Login just gets terminal"
date: 2010-01-05
forum: Desktop Environments
---

### Post by DangerFace on 2010-01-05
My issue is that when I log in, with any user, all I get is a terminal in the top left of the screen (see attached .png). I don't really know what has caused this - I think I was messing around with nautilus before the boot that ended with this, but it was a few days ago and I'm really not sure.If I try running a GUI-based program - say, I run 'firefox' in the terminal - then a firefox window appears, smaller than the screen but larger than the terminal area, without the window border (with minimize, close etc) so to exit I have to go to file > quit. 

I'm using Ubuntu 9.10 32 bit on a laptop. Any help in how to get back to my desktop would be greatly appreciated.

New to posting, if not to the site, so sorry if I screwed it up.

---

### Post by XubuRoxMySox on 2010-01-05
Try tryping "startx" (without the quotes), then once you're in a Gnome session, you can make it the default.

-Robin

---

### Post by SalahTr on 2010-01-05
On login screen choose **Gnome** in *session combobox *

---

### Post by DangerFace on 2010-01-05
"sudo startx" returns:
> Fatal server error:
Server is already active for display 0
     If this server is no longer running, remove /tmp/.X0-lock
     and start again.


Please consult blah blah

ddxSigGiveUp: Closing log
xinit: Server error.So, I rm /tmp/.X0-lock and try again, and this time I get:
> _XSERVTransSocketUNIXCreateListener: ...SocketCreateListener() failed
_XSERVTransMakeAllCOTSServerListeners: server already running

Fatal server error:
Cannot establish any listening sockets - Make sure an X server isn't already running

Please consult the wiki blah blah
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

ddxSigGiveUp: Closing logI don't know which bit of Xorg.0.log I should be looking at, but it basically has the _XSERV stuff from above plus:
> 
(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor
(WW) xf86OpenConsole:VT_GETSTATE failed: Bad file descriptor
ddxSigGiveUp: Closing logIs this bad? Is it fixable? I normally sort of enjoy sorting these things out, but I've got work due in and I'm having to do it on XP - my productivity is seriously suffering!

---

### Post by DangerFace on 2010-01-05
Forgot the other reply - is there still a session combobox on Karmic? Where would it be? I thought they got rid of it, and I can't find it.

---

### Post by SalahTr on 2010-01-05
> **DangerFace said:**
> Forgot the other reply - is there still a session combobox on Karmic? Where would it be? I thought they got rid of it, and I can't find it.
Here the login screen shot

---

### Post by DangerFace on 2010-01-06
Not sure where it saves screenshots of the login screen, but that's not what I get - I just have the on/off button in the bottom right and the accessibility button and that's it. Well, then I can click on the user and type in my password, but that's it.

---

### Post by DangerFace on 2010-01-06
OK, I'm giving up and reinstalling. Never mind.
Thanks anyways.

---

### Post by smoka on 2010-01-12
Hi, I've got exactly the same problem, had done a few things before (downgrading mythtv from 0.22 to 0.21 and uninstalled some of the included games in ubuntu) so not too sure what actually caused it.

Just wondering if anyone has any further ideas?

**SalahTr:** no, only thing I get at he bottom is just the lower right "Power", Date&Time, and that little man in a circle. Then, when I click on the user to login I get the "Language" and "Keyboard" options, but not that "Sessions" one I can see in your screen shot.

I've checked out a few of the logs, comparing against when it did work and can't say anything jumps out at all, so pretty stumped. Just hoping maybe someone had a similar problem and managed to fix it.

---

### Post by smoka on 2010-01-13
**FIXED...**  :P

As I suspected it was something I must have uninstalled, chose to install the gnome desktop again to see what was missing.

```
sudo aptitude install ubuntu-desktop
```

Chose to install it all, rebooted and everything is back to normal.

**SalahTr: **BTW, Once this was all installed again I did actually get that "Sessions" option at the bottom of the login screen.

Well, the following is what was missing, and one of these definitely caused the problem...

```
The following NEW packages will be installed:
  aisleriot{a} evolution evolution-common{a} evolution-couchdb 
  evolution-data-server{a} evolution-data-server-common{a} 
  evolution-documentation-en{a} evolution-exchange evolution-indicator 
  evolution-plugins{a} evolution-webcal{a} gnobots2{a} gnome-applets 
  gnome-games gnome-mahjongg{a} gnome-panel{a} gnome-session{a} 
  gnome-sudoku{a} gtali{a} indicator-applet{a} indicator-applet-session 
  indicator-messages{a} indicator-session{a} libedataserverui1.2-8{a} 
  ubuntu-desktop 
0 packages upgraded, 25 newly installed, 0 to remove and 1 not upgraded.
Need to get 13.8MB of archives. After unpacking 85.1MB will be used.
Do you want to continue? [Y/n/?]
```

---

