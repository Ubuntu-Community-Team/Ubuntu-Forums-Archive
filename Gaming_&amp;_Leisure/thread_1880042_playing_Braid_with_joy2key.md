---
title: "playing Braid with joy2key"
date: 2011-11-12
forum: Gaming &amp; Leisure
---

### Post by jarl-haggerty on 2011-11-12
I found a tutorial for mapping PS3 controller buttons to keyboard buttons,

[http://ubuntuforums.org/showthread.php?t=646564&highlight=joy2key](http://ubuntuforums.org/showthread.php?t=646564&highlight=joy2key)

And it seems to work but Braid doesn't seem to respond to joy2key's input.  I run this command and then I start braid,

```
sleep 10 && joy2key -config braid "Braid"
```And this is my .joy2keyrc file,

```
COMMON
-X
-dev /dev/input/js0
-thresh -16383 16383 -16383 16383 -16383 16383 -16383 16383 -16383 16383
-16383 16383 -16383 16383 -16383 16383 -16383 16383 -16383 16383 -16383
16383 -16383 16383 -16383 16383 -16383 16383 -16383 16383 -16383 16383
-16383 16383 -16383 16383 -16383 16383 -16383 16383 -16383 16383 -16383
16383 -16383 16383 -16383 16383 -16383 16383 -16383 16383 -16383 16383
-16383 16383

START braid
-X
-buttons r r r r Up Right Down Left r r r r r Shift_L z
```Braid is unresponsive to my controller but joy2key seems to be doing something,

```
jarl@jarl-U36JC:~$ sleep 10 && joy2key -config braid "Braid"
joy2key - reads joystick status and dispatches keyboard events
By Peter Amstutz (tetron@interreality.org)
This is free software under the GNU General Public License (GPL v2)
              (see COPYING in the joy2key archive)
You are welcome to use/modify this code, and please e-mail me
if anything cool comes of it!
Version: 1.6.3   Binary built on Dec 22 2009 at 13:45:44

argtokey:read key r dblcheck r
arg2key fed with r r is a lower => 0
argtokey:read key r dblcheck r
arg2key fed with r r is a lower => 0
argtokey:read key r dblcheck r
arg2key fed with r r is a lower => 0
argtokey:read key r dblcheck r
arg2key fed with r r is a lower => 0
argtokey:read key Up dblcheck Up
arg2key fed with Up Up is a lower => 0
argtokey:read key Right dblcheck Right
arg2key fed with Right Right is a lower => 0
argtokey:read key Down dblcheck Down
arg2key fed with Down Down is a lower => 0
argtokey:read key Left dblcheck Left
arg2key fed with Left Left is a lower => 0
argtokey:read key r dblcheck r
arg2key fed with r r is a lower => 0
argtokey:read key r dblcheck r
arg2key fed with r r is a lower => 0
argtokey:read key r dblcheck r
arg2key fed with r r is a lower => 0
argtokey:read key r dblcheck r
arg2key fed with r r is a lower => 0
argtokey:read key r dblcheck r
arg2key fed with r r is a lower => 0
argtokey:read key Shift_L dblcheck Shift_L
arg2key fed with Shift_L Shift_L is a lower => 0
argtokey:read key z dblcheck z
arg2key fed with z z is a lower => 0
Initialization complete, entering main loop, ^C to exit...
iscap is now 0  sendkey: button_upper: 0 keycode  0x000034  52   sendkey: keysym z
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x000034  52   sendkey: keysym z
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x000072  114   sendkey: keysym Right
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x000072  114   sendkey: keysym Right
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x00006f  111   sendkey: keysym Up
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x000071  113   sendkey: keysym Left
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x00006f  111   sendkey: keysym Up
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x00006f  111   sendkey: keysym Up
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x00006f  111   sendkey: keysym Up
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x00006f  111   sendkey: keysym Up
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x000071  113   sendkey: keysym Left
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x00006f  111   sendkey: keysym Up
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x000072  114   sendkey: keysym Right
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x00006f  111   sendkey: keysym Up
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x000072  114   sendkey: keysym Right
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x000071  113   sendkey: keysym Left
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x000071  113   sendkey: keysym Left
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x000072  114   sendkey: keysym Right
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x00006f  111   sendkey: keysym Up
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x00006f  111   sendkey: keysym Up
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x000072  114   sendkey: keysym Right
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x000071  113   sendkey: keysym Left
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x000071  113   sendkey: keysym Left
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x00006f  111   sendkey: keysym Up
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x00001b  27   sendkey: keysym r
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x00001b  27   sendkey: keysym r
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x000032  50   sendkey: keysym Shift_L
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x000071  113   sendkey: keysym Left
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x00001b  27   sendkey: keysym r
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x00001b  27   sendkey: keysym r
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x000032  50   sendkey: keysym Shift_L
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x000071  113   sendkey: keysym Left
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x00001b  27   sendkey: keysym r
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x000072  114   sendkey: keysym Right
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x00006f  111   sendkey: keysym Up
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x000072  114   sendkey: keysym Right
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x00001b  27   sendkey: keysym r
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x00001b  27   sendkey: keysym r
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x000071  113   sendkey: keysym Left
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x00006f  111   sendkey: keysym Up
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x00001b  27   sendkey: keysym r
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x00001b  27   sendkey: keysym r
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x000071  113   sendkey: keysym Left
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x00001b  27   sendkey: keysym r
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x000074  116   sendkey: keysym Down
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x000072  114   sendkey: keysym Right
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x000074  116   sendkey: keysym Down
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x00001b  27   sendkey: keysym r
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x00001b  27   sendkey: keysym r
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x000034  52   sendkey: keysym z
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x00006f  111   sendkey: keysym Up
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x000072  114   sendkey: keysym Right
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x00001b  27   sendkey: keysym r
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x00001b  27   sendkey: keysym r
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x000071  113   sendkey: keysym Left
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x000034  52   sendkey: keysym z
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x00001b  27   sendkey: keysym r
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x000071  113   sendkey: keysym Left
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x00001b  27   sendkey: keysym r
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x00001b  27   sendkey: keysym r
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x00006f  111   sendkey: keysym Up
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x000072  114   sendkey: keysym Right
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x000072  114   sendkey: keysym Right
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x00001b  27   sendkey: keysym r
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x000072  114   sendkey: keysym Right
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x00001b  27   sendkey: keysym r
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x000072  114   sendkey: keysym Right
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x00001b  27   sendkey: keysym r
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x000072  114   sendkey: keysym Right
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x00001b  27   sendkey: keysym r
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x000072  114   sendkey: keysym Right
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x000071  113   sendkey: keysym Left
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x00001b  27   sendkey: keysym r
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x000071  113   sendkey: keysym Left
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x000072  114   sendkey: keysym Right
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x00006f  111   sendkey: keysym Up
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x000072  114   sendkey: keysym Right
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x00001b  27   sendkey: keysym r
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x000071  113   sendkey: keysym Left
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x00001b  27   sendkey: keysym r
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x00001b  27   sendkey: keysym r
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x000071  113   sendkey: keysym Left
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x00006f  111   sendkey: keysym Up
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x000072  114   sendkey: keysym Right
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x000072  114   sendkey: keysym Right
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x000071  113   sendkey: keysym Left
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x00006f  111   sendkey: keysym Up
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x00001b  27   sendkey: keysym r
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x00001b  27   sendkey: keysym r
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x00006f  111   sendkey: keysym Up
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x00001b  27   sendkey: keysym r
state hex 10
iscap is now 0  sendkey: button_upper: 0 keycode  0x000071  113   sendkey: keysym Left
state hex 10

Window die caught, cleaning up & quitting.
```

---

### Post by weasel fierce on 2011-11-13
I'll try and check with Braid later. I generally use rejoystick rather than joy2key. Not sure if it's better or anything but it's always worked for me.

---

### Post by jarl-haggerty on 2011-11-15
I just tried qjoypad and it's working well.  Also, in case anyone has the same problem I did, I kept left and right clicking on the tray icon and the menu to add and edit layouts wouldn't come up, just use the --notray option.

---

