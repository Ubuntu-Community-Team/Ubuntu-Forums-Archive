---
title: "avoid xscreensaver unlock screen when switching from user"
date: 2012-07-07
forum: Desktop Environments
---

### Post by cdevos on 2012-07-07
Hello,

I have Lubuntu 12.04 installed on a macmini and here is what bothers me: when I switch from one user to the other one, I have to type twice my password: once for LXDE, and once for xscreensaver. I used xscreensaver-demo to ensure that the screen is not locked, but it doesn't change anything. Here is the .xscreensaver:

```
timeout:        0:10:00
cycle:          0:10:00
lock:           False
lockTimeout:    0:00:00
passwdTimeout:  0:00:30
visualID:       default
installColormap:    True
verbose:        False
timestamp:      True
splash:         True
splashDuration: 0:00:05
demoCommand:    xscreensaver-demo
prefsCommand:   xscreensaver-demo -prefs
nice:           10
memoryLimit:    0
fade:           True
unfade:         False
fadeSeconds:    0:00:03
fadeTicks:      20

captureStderr:  True
ignoreUninstalledPrograms:False
font:           *-medium-r-*-140-*-m-*
dpmsEnabled:    False
dpmsQuickOff:   False
dpmsStandby:    2:00:00
dpmsSuspend:    2:00:00
dpmsOff:        4:00:00
grabDesktopImages:  False
grabVideoFrames:    False
chooseRandomImages: True
imageDirectory: /home/carl/Pictures/screensaver

mode:           blank
selected:       16

textMode:       url
textLiteral:    XScreenSaver
textFile:
textProgram:    fortune
textURL:        http://fridge.ubuntu.com/node/feed

programs:                                                                     \
                                maze -root                                  \n\
- GL:                           superquadrics -root                         \n\
<snip>
```

Any way to avoid typing the second time my password ?

Thanks in advance.

---

### Post by nyktovus on 2013-01-26
*bump* i'm having this issue as well in lubuuntu 12.10.. its really obnoxious.

---

