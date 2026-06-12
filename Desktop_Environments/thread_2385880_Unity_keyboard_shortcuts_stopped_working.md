---
title: "Unity keyboard shortcuts stopped working"
date: 2018-02-26
forum: Desktop Environments
---

### Post by veddox on 2018-02-26
Hi everyone,

booting my laptop (Thinkpad T420) last night, Unity failed to start after login. I rebooted via commandline and everything seemed to start normally, except that several keyboard shortcuts related to the desktop environment suddenly didn't work anymore. (Shift workspace up/down/right/left, move windows to neighbouring workspace, dock window right/left.) I rebooted a couple of times and installed all pending updates, but the problem persists. System settings indicate that the keyboard shortcuts haven't changed.

Has anybody experienced something similar? Or does anybody have a clue what's causing it? All help appreciated :-)

EDIT: This is not a keyboard shortcut problem. The affected options also don't work with the mouse. (E.g. dragging a window to the side of the screen should "dock" it there - it doesn't anymore.)

---

### Post by Frogs Hair on 2018-02-26
Try reseting compiz.

[https://ubuntuforums.org/showthread.php?t=2382909&highlight=reset+unity](https://ubuntuforums.org/showthread.php?t=2382909&highlight=reset+unity)

---

### Post by veddox on 2018-02-26
Thanks for the hint, but I'm afraid it didn't work. Tried resetting, rebooted, tried resetting with sudo, rebooted again, still nothing :-(

---

### Post by Frogs Hair on 2018-02-27
Unity Reset:```
 setsid unity
```

---

### Post by veddox on 2018-02-27
Doesn't work either...

---

### Post by deadflowr on 2018-02-27
I wonder if you somehow moved into low-graphics-mode.
I'm not really sure how to tell except look at the old *unity supports this system* command
```
/usr/lib/nux/unity_support_test -p
```
The output should show this for full unity  in 3d
```
Not software rendered:    yes
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       yes
```

If anything is No, then you would be in low graphics mode, which may account for the oddness.

However this isn't much more than throwing something and seeing if it sticks or not.

---

### Post by veddox on 2018-02-28
Thank you for all your efforts! The output to the command above is as expected. Browsing through the syslogs, I came upon the following line:

```
Feb 27 21:23:08 <host> org.gnome.ScreenSaver[1513]: ** (gnome-screensaver:1869): WARNING **: Couldn't get presence status: The name org.gnome.SessionManager was not provided by any .service files
```

At first I thought that that must be the cause (however one would go about fixing it), but then I discovered that the warning already appears in logs from before the problem started. Still, it might be relevant.

---

### Post by vasa1 on 2018-02-28
Please run```
sudo apt-get update
```followed by```
sudo apt-get dist-upgrade
```You can abort the second command at the "Y/n" prompt if you are unsure of proceeding. Are there any errors or warnings in the output?

---

### Post by vasa1 on 2018-02-28
See [https://askubuntu.com/questions/995819/touchpad-gestures-and-holding-keys-does-not-work](https://askubuntu.com/questions/995819/touchpad-gestures-and-holding-keys-does-not-work) in case anything there relates to your issue.

---

### Post by q-ms on 2018-08-11
I have the exact same issue with a Lenovo T530. Unity crashed after startup, and rebooting brings me to a desktop where neither window docking nor switching workspaces works anymore. 

Even if I re-assign shortcuts for workspaces, ie. CTRL+F1, CTRL+F2 etc, they are ignored and do not work.

If I click on a starter symbol from an app that is opened in another workspace, nothing happens either, instead of switching over to the app's workspace. 

Very irritating.

---

### Post by owenjonesuk01 on 2018-10-18
I had exactly this problem this morning. I eventually found the answer when I realised it wasn't just a keyboard shortcut problem, as some operations with the mouse didn't work either. Using ccsm to turn on Desktop Wall (in the Desktop section) made my shortcuts start working again. [https://askubuntu.com/a/820377](https://askubuntu.com/a/820377)

I also had to to turn on Grid in the Window Management section to re-enable the ability to snap windows to the edge of the screen.

---

