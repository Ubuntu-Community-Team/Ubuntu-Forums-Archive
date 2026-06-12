---
title: "Configuring a ps2 guitar hero with adapter for ubuntu - xboxdrv"
date: 2014-09-17
forum: Gaming &amp; Leisure
---

### Post by gabaod on 2014-09-17
Hi there.

I have a EMS USB Joypad 2 that gives me 2 ps2 controller inputs and converts it into a USB connection.

I am trying to map the keys and not exactly sure how to configure the part you strum up and down.  Not worried about the whammy bar as I hear its near impossible to get to work via a ps2 port.

I have found out this information so far:
/dev/input/event4
green = BTN_PINKIE
red = BTN_THUMB
yellow = BTN_TRIGGER
blue = BTN_THUMB2
orange = BTN_TOP
start = BTN_BASE4
select = BTN_BASE3

but for the strum button that goes up or down it gives me this output:
Event: time 1410975575.534160, type 4 (EV_MSC), code 4 (MSC_SCAN), value 9000d
Event: time 1410975575.534160, type 1 (EV_KEY), code 300 (?), value 1
Event: time 1410975575.534160, type 3 (EV_ABS), code 1 (ABS_Y), value 0
Event: time 1410975575.534160, type 3 (EV_ABS), code 2 (ABS_Z), value 0
Event: time 1410975575.534160, -------------- SYN_REPORT ------------
Event: time 1410975575.718160, type 4 (EV_MSC), code 4 (MSC_SCAN), value 9000d
Event: time 1410975575.718160, type 1 (EV_KEY), code 300 (?), value 0
Event: time 1410975575.718160, type 3 (EV_ABS), code 1 (ABS_Y), value 128
Event: time 1410975575.718160, type 3 (EV_ABS), code 2 (ABS_Z), value 128
Event: time 1410975575.718160, -------------- SYN_REPORT ------------
Event: time 1410975630.430324, type 4 (EV_MSC), code 4 (MSC_SCAN), value 9000f
Event: time 1410975630.430324, type 1 (EV_KEY), code 302 (?), value 1
Event: time 1410975630.430324, type 3 (EV_ABS), code 1 (ABS_Y), value 255
Event: time 1410975630.430324, type 3 (EV_ABS), code 2 (ABS_Z), value 255
Event: time 1410975630.430324, -------------- SYN_REPORT ------------
Event: time 1410975630.646324, type 4 (EV_MSC), code 4 (MSC_SCAN), value 9000f
Event: time 1410975630.646324, type 1 (EV_KEY), code 302 (?), value 0
Event: time 1410975630.646324, type 3 (EV_ABS), code 1 (ABS_Y), value 128
Event: time 1410975630.646324, type 3 (EV_ABS), code 2 (ABS_Z), value 128

The first one is strumming up, and the second would be strumming down but I dont see any button name associated with it.   So I am not sure how to pass that info along to xboxdrv to map it properly.   

Per the guide I was following on steam it says this, which has no reference to a guitar input.
5. Initializing xboxdrv
If you have a PS3  controller, you don't have to map your controller nor nothing. Just  initialize xboxdrv like this and everything will be working:
*# xboxdrv --silent --detach-kernel-driver*
If  you have any other controller, now that you have all your buttons and  axis mapped, you must initialize xboxdrv properly. To do so, you'll have  to initialize it like this:
*# xboxdrv --evdev [EVENT] --evdev-absmap [ABS MAP] --axismap [AXIS MAP] --evdev-keymap [BUTTONS MAP] --mimic-xpad --silent &*
[EVENT]  is the event associated with your controller (section 3 of this post)  and [ABS MAP], [AXIS MAP] and [BUTTONS MAP] are your controller mapping  (section 4 of this post). In my case, my PS2 controller + USB adapter is  associated with /dev/input/event11 and has the above mapping, so I  initialize xboxdrv like this:
*# xboxdrv --evdev  /dev/input/event11 --evdev-absmap  ABS_X=x1,ABS_Y=y1,ABS_RZ=x2,ABS_Z=y2,ABS_HAT0X=dpad_x,ABS_HAT0Y=dpad_y  --axismap -Y1=Y1,-Y2=Y2 --evdev-keymap  BTN_TOP=x,BTN_TRIGGER=y,BTN_THUMB2=a,BTN_THUMB=b,BTN_BASE3=back,BTN_BASE4=start,BTN_BASE=lb,BTN_BASE2=rb,BTN_TOP2=lt,BTN_PINKIE=rt,BTN_BASE5=tl,BTN_BASE6=tr  --mimic-xpad --silent &*

Note that if you have a PS2  controller too, you will initialize xboxdrv exactly the same way I do,  except for the event, which might be another one.


Any help would be appreciated ;)

---

### Post by deadflowr on 2014-09-17
Moved to [I][B]Gaming and Leisure
[/B][/I]
Even if you're going to use the going to use the device for general purposes, the people who post in this section will probably have a better understanding of xboxdrv and what needs to be done than anywhere else on the forums.

---

### Post by gabaod on 2014-09-17
K thanks :)

---

