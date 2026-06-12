---
title: "Gamepad set up (for the humble indie bundle 2) or alternative"
date: 2010-12-15
forum: Gaming &amp; Leisure
---

### Post by balta on 2010-12-15
Hi there!
So I just got the humble indie bundle 2 and I'm ready do play braid all way down again (already finished it a few times ... but this time is ubuntu time!)
But I'm having problems setting up my gamepad :(
The pad is this [SpeedLink sl-6555-sbk xBox 360 style wired usb pad.]("http://www.speedlink.com/?p=2&cat=3132&pid=22714&paus=1") and here follows what I did.
First of all I plugged it into the computer
Center red led flashes for a sec and then turns off (note: on windows is on while working).
I looked for something in administration and preferences (something like gaming peripherals lol) but had no luck.
I installed package joystick and ran 
```
~$ jscal /dev/input/js0

Joystick has 7 axes and 10 buttons.
Correction for axis 0 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 1 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 2 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 3 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 4 is broken line, precision is 0.
Coeficients are: 112, 142, 5534751, 5534751
Correction for axis 5 is broken line, precision is 0.
Coeficients are: 0, 0, 536870912, 536870912
Correction for axis 6 is broken line, precision is 0.
Coeficients are: 0, 0, 536870912, 536870912

```
and then
```
~$ jstest /dev/input/js0

Driver version is 2.1.0.
Joystick (ACRUX USB GAMEPAD 8116) has 7 axes (X, Y, Z, Rz, Throttle, Hat0X, Hat0Y)
and 10 buttons (Trigger, ThumbBtn, ThumbBtn2, TopBtn, TopBtn2, PinkieBtn, BaseBtn, BaseBtn2, BaseBtn3, BaseBtn4).
Testing ... (interrupt to exit)
Axes:  0:-32767  1:-32767  2:-32767  3:-32767  4:-32767  5:     0  6:     0 Buttons:  0:off  1:off  2:off  3:off  4:off  5:off  6:off  7:off  8:off  9:off

```
Actually all the screens looked nice and geeky but not a single response from any input from the pad =(
Now I don't know what to do...
If someone can help me solving this, I would be very grateful.
If not, at least can someone confirm that a wired genuine xbox pad works out of the box?

Thanks for your time!
Truly yours,

---

### Post by balta on 2010-12-16
Added the POLL!
Please explain how you did set-up\configured or whatever you did to make the pad work.

...
also: BUMP! :)

---

### Post by cchhrriiss121212 on 2010-12-17
Gamepad support has to be built into the software you want to use it with. I think the only game in the HIB2 to do so is Cortex Command. 
To use a gamepad you just need to plug it in, no config/installation required. But I don't know whether all gameads are fully supported.

---

### Post by balta on 2010-12-17
Thanks for the response!
I expected Braid to be playable with a pad being originally born for xBox ... to bad, however I think I do have a compatibility problem with my pad =(
I'm afraid I'll play those on windoze, too bad :(

---

### Post by Isaacgallegos on 2010-12-21
Yeah,  Cortex Command will not find my gamepads, which is the first time I've ever had this problem with my current setup. There are no problems with the same setup in Windows. 

I'm trying my best to find a solution. If I find one I'll post.

---

### Post by clayton2 on 2010-12-21
I thought I had read somewhere that Braid works out of the box with an official wired Xbox 360/Games for Windows controller.  But I'm not sure if that's just the Windows version of Braid, or if that works for the Linux version too. I'm not sure.

I tried playing Braid with the keyboard, but my hand would get cramped.  I have a super old Microsoft SideWinder controller, and got rejoystick from the repos, and just assigned [Shift] to the X button, etc.  It works fine.  I would still like to see Canonical sell an officially branded Ubuntu gamepad. lol

---

### Post by balta on 2010-12-21
Yup! Glad I'm not the only having this issue!
However my problem is indeed with the pad itself (not with the games), I think it just doesn't work with ubuntu :( for now I'm using it under Steam with x360ce ;)

---

### Post by metalf8801 on 2010-12-23
Take a look at 
Qjoypad [http://www.playdeb.net/updates/ubuntu/10.10/?q=qjoypad](http://www.playdeb.net/updates/ubuntu/10.10/?q=qjoypad)
and
QtSixA [https://launchpad.net/~falk-t-j/+archive/qtsixa](https://launchpad.net/~falk-t-j/+archive/qtsixa)

I've been able to use Qjoypad to set up my ps3 controller to work with Open Sonic and Supper Tux 

I hope this helps and feel free to ask me if you have any questions 
Dan

---

### Post by balta on 2010-12-24
New xbox 360 compatible pad a qjoystick works just perfect!
bye bye windoze :D
(too bad my old pad doesn't seem to work at all, no multiplayer for me under ubuntu :()

Thanks everybody and particularly metalf8810

---

