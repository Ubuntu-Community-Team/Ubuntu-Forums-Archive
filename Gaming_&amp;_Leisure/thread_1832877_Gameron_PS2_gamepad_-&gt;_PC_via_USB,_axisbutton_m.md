---
title: "Gameron PS2 gamepad -&gt; PC via USB, axis/button mismatch"
date: 2011-08-25
forum: Gaming &amp; Leisure
---

### Post by KalithDemoren on 2011-08-25
Hi,

I just received an adaptator that allows me to plug my old PlayStation 2 controller into an USB port and use it to play emulated game.
The adpatator is from *Gameron*, but there is no clear product name (in french : "Adaptateur Manette PS2 > PS3, Compatible Sony PS3 / PC"). It has a "Gamepad" <-> "Wheel" switch on its side.

It works as soon as it is plugged, but it is badly recognized...

Using the "Gamepad" mode :
I've been playing with **jstest** for hours now, and managed to write down an axis/button map. Here is the output of jstest :
> Joystick (Sony PLAYSTATION(R)3 Controller) has 30 axes (X, Y, Z, Rz, Hat0X, Hat0Y, (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null), (null))
and 13 buttons (Trigger, ThumbBtn, ThumbBtn2, TopBtn, TopBtn2, PinkieBtn, BaseBtn, BaseBtn2, BaseBtn3, BaseBtn4, BaseBtn5, BaseBtn6, BtnDead).... and the home made button/axis map :
```
# Axis :
0  : analog left horizontal
1  : analog left vertical
2  : analog right horizontal
3  : analog right vertical
4-9  : ??
10 : directional pad top
11 : directional pad right
12 : directional pad bottom
13 : ?? (supposedly "directional pad left", but doesn't respond to pressure)
14 : L2
15 : R2
16 : L1
17 : R1
18 : triangle
19 : circle
20 : cross
21 : square
22-29 : ??

# Buttons :
0  : select
1  : analog left
2  : analog right
3  : start
4  : directional pad top
5  : directional pad right
6  : directional pad bottom
7  : directional pad left
8  : L2
9  : R2
10 : L1
11 : R1
12 : triangle
```As you can see, all buttons are interpreted as both an axis (pressure sensitive : -32767 when released and +32767 when pressed) and a button (0/1), yet "circle", "cross" and "square" are missing from the button list... They should probably appear after "triangle" in the list, that is as buttons 13, 14 and 15 respectively.
Plus the "left" arrow of the directional pad doesn't seem to be recognized as an axis (couldn't get any input from axis 13).

**lsusb** reports :
> Bus 002 Device 012: ID 054c:0268 Sony Corp. Batoh DeviceThe "Wheel" mode is much simpler, and is not recognized as a Sony controller. From **jstest** :
> Joystick (Logitech Logitech Driving Force) has 4 axes (X, Y, Hat0X, Hat0Y)
and 12 buttons (Trigger, ThumbBtn, ThumbBtn2, TopBtn, TopBtn2, PinkieBtn, BaseBtn, BaseBtn2, BaseBtn3, BaseBtn4, BaseBtn5, BaseBtn6).... and the button/axis map :
```
Axis :
0  : analog left horizontal
1  : analog right vertical
2  : left-right
3  : top-bottom

Buttons :
0  : cross
1  : square
2  : circle
3  : triangle
4  : R1
5  : L1
6  : R2
7  : L2
8  : start
9  : select
10 : analog left
11 : analog right
```All buttons work fine in this mode, but the analog sticks are working strangely : only the horizontal axis of the left stick and vertical axis of the right one are recognized... That's not handy at all. Plus the directional pad is not pressure sensitive (values are either -32767, 0 or +32767).

I'm using Ubuntu 11.04 32bit with linux-image-2.6.38-11.
I've tried with two different PS2 controllers and the result is the same (actually, the other one is a bit broken, and the directional pad doesn't even work).

Am I screwed or can I change the driver to support my adapatator ?

Thank you for your assistance.

---

### Post by KalithDemoren on 2011-08-27
I know it may sound too technical for this forum, but all threads regarding PS2 controllers that I've found were there.
Do you know a better place where I might post this ?

**Edit** : I had the opportunity to test it on a Windows XP machine.
The adaptator in "Gamepad" mode was recognized as soon as it was plugged  in (no additional driver needed), and all buttons and axis were  properly mapped (at least the two analog axis on X and Y). It reports 13  buttons as well, with the following button map. I couldn't activate the  13th button though, so I don't know what it is mapped to, maybe the  analog button ?
```
0  : triangle
 1  : circle
 2  : cross
 3  : square
 4  : L1
 5  : R1
 6  : L2
 7  : R2
 8  : select
 9  : start
10 : analog left
11 : analog right
12 : ? (analog button ?)
```I don't understand how it is possible for the button mapping to be so different between the two OSes.

I have good programming skills, so I downloaded the current linux kernel source to see if I could understand something from the driver code, but it seems I couldn't locate the proper files. The controller apparently needs the "hid_sony" module (/dev/input/js0 disappears if I **modprobe -r hid_sony**), but the source code of drivers/hid/hid-sony.c contains no interesting information.
Where does the OS translate the USB input to button/axis events ?

**Edit** : bug report submitted here :
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/836335](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/836335)

---

