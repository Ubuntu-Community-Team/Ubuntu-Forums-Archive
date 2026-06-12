---
title: "xboxdrv Back/Start &amp; Trigger Buttons Problem"
date: 2013-01-22
forum: Gaming &amp; Leisure
---

### Post by d10sfan on 2013-01-22
I've been using xboxdrv, trying to get some games working with my wireless 360 controller and it works great except the Back, Start, Left Stick Button, and Right Stick Buttons do not work properly.

Noticed in one of the games I was trying, Serious Sam 3, that the Right Stick click is seen as the left stick click, and Back is seen as Left stick click. The same thing happens in Trine 2 as well. 

[edit] Trine 2 is no longer doing this (start and back work fine now, strange)

The rest of the buttons (color buttons, dpad, etc) work fine.

The command I'm using for xboxdrv is:

```
sudo xboxdrv --silent --mimic-xpad
```

---

### Post by xREDEMPTIONx on 2013-01-22
You can tell xboxdrv to load a custom config file instead and make the adjustments you need there. Also, I think you'll need to unload the xpad module as well. Here's an example config you can start with and tweak as needed. Just copy and paste this into an empty text document and name it whatever you want.

```

[xboxdrv]
silent = true
ui-clear = true
deadzone=4000
deadzone-trigger = 15%

[ui-buttonmap]
A=BTN_A
B=BTN_B
X=BTN_X
Y=BTN_Y

START=BTN_START
GUIDE=BTN_MODE
BACK=BTN_SELECT

LB=BTN_TL
RB=BTN_TR

TL=BTN_THUMBL
TR=BTN_THUMBR

[ui-axismap]
X1=ABS_X
Y1=ABS_Y

X2=ABS_RX
Y2=ABS_RY 

LT=ABS_Z
RT=ABS_RZ

DPAD_X = ABS_HAT0X
DPAD_Y = ABS_HAT0Y

# EOF #

```Then to start xboxdrv with this config-

```

xboxdrv -c /PATH/TO/YOUR/FILE --type xbox360-wireless --detach-kernel-driver

```

---

