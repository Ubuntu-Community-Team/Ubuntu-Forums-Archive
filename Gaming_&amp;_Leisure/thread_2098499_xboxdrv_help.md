---
title: "xboxdrv help?"
date: 2012-12-26
forum: Gaming &amp; Leisure
---

### Post by madinc on 2012-12-26
Can somebody show me a example of a .xboxdrv configuration file for car racing games like torcs, supertuxkart, etc i have tried  but no success please help it's for my kid.
I have the xbox 1 controller i looked in many places but i just can't make the sensitivity work.
I also looked here
[https://github.com/Grumbel/xboxdrv/tree/master/examples](https://github.com/Grumbel/xboxdrv/tree/master/examples)
and here
[http://manpages.ubuntu.com/manpages/precise/man1/xboxdrv.1.html](http://manpages.ubuntu.com/manpages/precise/man1/xboxdrv.1.html)
but i just don't know how to do it help please.

---

### Post by kreggz on 2012-12-29
Can you play these games using wasd with the keyboard? If so it would be easy to make the config.

---

### Post by Th3J0k3r on 2012-12-29
have you tried messing with the scroll speed if your running on vbox/vmware/etc?

---

### Post by kreggz on 2012-12-29
try this

# Tux Kart
# DPAD and Left Joystick only move left and right
# X = Forward
# A = Break/Backward
# Y = Look Back
# B = Rescue (respawn)
# Top right buttons = Fire
# Top left buttons = Nitro
# Start = enter
# Menu = escape

[xboxdrv]
ui-clear=true
trigger-as-button = true

[ui-axismap]
x1=KEY_LEFT:KEY_RIGHT
y1=

x2^dead:4000 = REL_X:750:-1
y2^dead:4000 = REL_Y:750:-1

[ui-buttonmap]
a = KEY_DOWN
b = KEY_BACKSPACE
x = KEY_UP
y = KEY_B
lt = KEY_N
rt = KEY_SPACE

rb = KEY_N
lb = KEY_SPACE

#tl = KEY_BACKSPACE
#tr = KEY_SPACE

[ui-buttonmap]
du = 
dr = KEY_RIGHT
dd = 
dl = KEY_LEFT

# lt = KEY_VOLUMEDOWN
# rt = KEY_VOLUMEUP

[ui-buttonmap]
start = KEY_ENTER
back  = KEY_ESC
# guide = KEY_ESC

# EOF #

---

### Post by madinc on 2012-12-31
> **kreggz said:**
> try this

Hi thank you for helping but what i want is the steering, gas and brakes to be sensitive i already had this for supertuxkart with left stick for steering and triggers for gas and brakes.

```
[xboxdrv]
silent=true
deadzone=6000
trigger-as-button=true

[ui-axismap]
x1=KEY_LEFT:KEY_RIGHT

[ui-buttonmap]
a=KEY_N
b=KEY_SPACE
x=KEY_V
y=KEY_B

[ui-buttonmap]
lb=
rb=KEY_BACKSPACE

[ui-buttonmap]
lt=KEY_DOWN
rt=KEY_UP

[ui-buttonmap]
back=
start=KEY_ESC
# EOF #
 
```But what i want is this:
```
[ui-axismap]
x1=KEY_LEFT:KEY_RIGHT
```and this:
```
[ui-buttonmap]
lt = KEY_DOWN
rt = KEY_UP

```to be sensitive if you know how it would be great thanks.

---

### Post by xREDEMPTIONx on 2012-12-31
Hi, try removing the line 

trigger-as-button=true

Then for the analog sticks and triggers (this is mine for 360 controller, not sure about original xbox controller)

[ui-axismap]
X1=ABS_X
Y1=ABS_Y

X2=ABS_RX
Y2=ABS_RY 

LT=ABS_Z
RT=ABS_RZ

These might not be exactly what you need because there are other options for axis such as 

LT = ABS_BRAKE
RT = ABS_GAS

---

### Post by madinc on 2013-03-15
Hi there sorry for the late reply this was for my kid and i ended up buying him a playstation since i only play fps  i never tried your solution so i don't know if it works but thanks anyway.

---

