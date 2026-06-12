---
title: "Nunchuk as joystick in Mupen"
date: 2010-01-20
forum: Gaming &amp; Leisure
---

### Post by Claritux on 2010-01-20
I've successfully been able to map my wiimote + nunchuk to keyboard inputs using xwii or wminput, and I'm at the moment happily playing Super Mario 64 in Mupen 8). The only minor problem I have is that the joystick on the nunchuck isn't acting like an actual joystick, but just as normal keyboard arrows. (Which means that I'm not able to sneak up on sleeping plants :P). Is there any way I can configure Mupen to use my nunchuk as a joystick input?

---

### Post by Maheriano on 2010-01-20
I got to get in on this too. I use Mupen to play some other games.

---

### Post by Claritux on 2010-01-23
Anyone?

BTW, here are the scripts I use for wminput and xwii, if anyone's interested:

Xwii:
[http://dl.dropbox.com/u/955480/Nunchuk%20N64.xwii](http://dl.dropbox.com/u/955480/Nunchuk%20N64.xwii)

Wminput:
[http://dl.dropbox.com/u/955480/N64](http://dl.dropbox.com/u/955480/N64)

---

### Post by Claritux on 2010-01-23
OK, I've found something called "wm2js" that supposedly is able to use the controller as a joystick, but I can't find any information about how to install or use it. Can anybody help?

[https://trac.v2.nl/browser/andres/wm2js](https://trac.v2.nl/browser/andres/wm2js)

---

### Post by Amagineer on 2010-01-27
I've got it compiled, but not working.

I checked it out from svn ```
svn checkout https://svn.v2.nl/andres/wm2js/
``` and after I installed its bluetooth dependency ```
sudo aptitude install libbluetooth-dev
``` I compiled it ```
cd wm2js
make
``` but running it only errored ```
./wm2js
Warning: Unable to open uinput device ; hint: 'modprobe uinput' ?!
Error: Registering the uinput device failed, aborting!

```And doing a ```
sudo modprobe uinput
``` and running it again (even as root) yielded the same results :(

---

### Post by Claritux on 2010-02-10
I got the same result after trying to compile.

However, looking into the wminput documentation ([http://abstrakraft.org/cwiid/browser/trunk/doc/wminput.list](http://abstrakraft.org/cwiid/browser/trunk/doc/wminput.list)) I found this:

```
# Nunchuk Axes
Nunchuk.Stick.X
Nunchuk.Stick.Y
```

I've tried to map this to different settings without getting any visible results.

Also, while googling I found this:
[http://wiki.mandriva.com/en/Docs/Hardware/Wiimote#Patching_WMD](http://wiki.mandriva.com/en/Docs/Hardware/Wiimote#Patching_WMD)
I think this proves it's possible, but I'm not skilled enough to find out how.

---

### Post by Claritux on 2010-02-28
*Bump*

---

### Post by Austin25 on 2010-02-28
I would love for this to get working, for I would like to play Zelda.
I think you can map the nunchuk joystick to a joystick, and the buttons to gamepad buttons, but not sure...

---

### Post by Claritux on 2010-03-14
*bump*

I did actually succeed in getting some sort of output by doing:

```
Nunchuk.Stick.X = ABS_X
Nunchuk.Stick.Y = ABS_Y
```

This made the mouse pointer place itself on the screen corresponding to the location of the stick on the controller. (E.g. if I put the stick up to the right on the nunchuk the mouse pointer will also go up and right, but once I let it go the mouse pointer will place itself back to the middle of the screen.)

---

### Post by Austin25 on 2010-03-25
'nother bump

---

### Post by xamar on 2010-04-11
> **Amagineer said:**
> I've got it compiled, but not working.
( ..... )
```
./wm2js
Warning: Unable to open uinput device ; hint: 'modprobe uinput' ?!
Error: Registering the uinput device failed, aborting!

```( ...)


It seems the path for the uinput device is not right. Open 'uinput.c' and modify line 29 to match this:
```
fd = open("/dev/uinput", O_RDWR);
```Recompile it:
```
make clean
make
```And try it again.

Sadly, for me, it seems it can't sync with the wiimote. All I get is this:
```
./wm2js 
Searching Wiimotes ; press 1+2 or the red SYNC button...
Error: Unable to establish controlling channel

```

---

### Post by Claritux on 2010-04-16
Same story for me, only that I had to use sudo to be able to use it. I even tried adding the bluetooth adress of my wiimote to the command without any results.

---

### Post by arrenlex on 2010-04-24
I got wm2js to work just fine... the bt address is hardcoded in wm2js.c on line 28. Just change it to the address of your wiimote (as discovered by sudo hcitool scan), compile, and run wm2js as root.

KDE's joystick calibration panel picks it up great. The nunchuck joystick is axis 7 and 8 I believe.

Now the problem for me is that mupen's input plugin doesn't react to the axis motions at all :(

---

### Post by Claritux on 2010-05-04
Confirmed. I'm able to calibrate it using jscal.
It maps the following functions:

Axis 0: up/down on the dpad
Axis 1: right/left on the dpad
Axis 2: tilt wiimote left/right
Axis 3: tilt wiimote up/down
Axis 4: tilt wiimote with buttons down/up
Axis 5: left/right on the nunchuck joystick
Axis 6: down/up on the nunchuck joystick

As mentioned, Mupen will unfortunately not pick up the nunchuck. I think it might be because it only registers input from axis 0 and 1. I'm able to pick up the dpad using the input plugin. Does anybody know how to make wm2js map the nunchuk to axis 0 and 1?

---

### Post by arrenlex on 2010-05-04
> **akshov said:**
> 
As mentioned, Mupen will unfortunately not pick up the nunchuck. I think it might be because it only registers input from axis 0 and 1. I'm able to pick up the dpad using the input plugin. Does anybody know how to make wm2js map the nunchuk to axis 0 and 1?

First thing I thought of too, but unfortunately that's not the issue.

Attached is a modified version of wm2js which only listens to the nunchuck x and y inputs. Therefore, there's only 2 axes.

Mupen still doesn't like it, though.

(Don't forget to change your bt address after downloading this tarball)

Cheers,
Alex

---

### Post by Claritux on 2010-05-04
Too bad :( Same thing over here
I did test it out in Neverball too. Worked with the Dpad, but not with the Nunchuck.

---

### Post by arrenlex on 2010-05-05
> **akshov said:**
> I did test it out in Neverball too. Worked with the Dpad, but not with the Nunchuck.

Is this the original wm2js or the modified one? The modified one shouldn't respond to the dpad at all.

---

### Post by Claritux on 2010-05-07
*Dpad worked with the original, nunchuk with neither of them.
Sorry for being unspecific #-o

---

### Post by arrenlex on 2010-05-16
Good news! I figured it out! :)

It's a scaling issue. wm2js outputs values in the range of about 30 (stick all the way left) to 220 (stick all the way right).

The problem is that most programs expect joysticks to emit in the range -32768 to 32767!

In fact, the emitted values were so tiny that they are completely within the range at which a normal joystick would be considered "at centre". So when mupen was listening to the joystick, the changes it detected were so tiny it basically decided the joystick hadn't moved at all.

I modified wm2js to scale the produced 30..220 value into the full -32768..32767 range. And now it works!!

Also note that, for my wiimote, when the stick was all the way to the right it stopped at about 30000 rather than 32767 (left was much closer). This caused Link to frequently walk instead of run for me. So I put in code to peg the stick all the way to the end if it's beyond 25000.

It should be fine, but if you're having problems with it, feel free to reduce\increase the peg threshold (nunchuck.c, scale_axis function).

Modified wm2js is attached. Don't forget to change your bt address, and have a lot of fun. :)

Cheers,
Alex

---

### Post by Claritux on 2010-06-12
That works great! Thank you! Now that my exams are almost over I'll finally be able to use it too :P

---

### Post by Tyr42 on 2010-12-29
I'm going to try and fix it up so that it can take the wiimote address from the command line.

I also want to extend it to working with the classic controller, unless someone else has already got that functionality?

---

### Post by arrenlex on 2010-12-29
Tyr42,

I can't find any license in the wm2js code. Perhaps we should get in touch with the original author and see what he wants wm2js licensed under. Then we would be able to move it into a sourceforge or google code project and have a proper collaborative development environment.

EDIT: Didn't look hard enough; it's in uinput.h. Looks like it's GPL2. I still think we should try contacting him before making a project out of this, to be polite.

---

### Post by Tyr42 on 2010-12-29
Well, I got it to accept the address from the command line.  Use it as wm2js -c 00:22:D7:78:83:EC or whatever.  I intend to add the ability to read from a file specified with -f, but I haven't finished that yet. Enjoy.

Preposting edit:
Oh I see that now.  Thanks for pointing that out.  I totally forgot about checking for anything like that:oops:  Sure, let's contact him.

---

### Post by antti64 on 2011-01-22
Hi!

I compiled wm2js. However I cannot connect to Wiimote. 

```
/Nintendo/wm2js$ ./wm2js -c 00:00
Searching Wiimotes ; press 1+2 or the red SYNC button...
Error: Unable to establish controlling channel

```

How I can found out Bluetooth address of Wiimote?

Antti

---

### Post by antti64 on 2011-01-22
> **antti64 said:**
> Hi!

I compiled wm2js. However I cannot connect to Wiimote. 

```
/Nintendo/wm2js$ ./wm2js -c 00:00
Searching Wiimotes ; press 1+2 or the red SYNC button...
Error: Unable to establish controlling channel

```

How I can found out Bluetooth address of Wiimote?

Antti

Stepping further:

```
hcitool scan
Scanning ...
	00:22:4C:8D:FF:F7	Nintendo RVL-CNT-01

wm2js -c 00:22:4C:8D:FF:F7
Searching Wiimotes ; press 1+2 or the red SYNC button...
Connection established! 0x7fff665a9560
Warning: Unable to open uinput device ; hint: 'modprobe uinput' ?!
Error: Registering the uinput device failed, aborting!
```

How to solve this?

Antti

---

### Post by arrenlex on 2011-01-22
> **antti64 said:**
> 
Warning: Unable to open uinput device ; hint: 'modprobe uinput' ?!
Error: Registering the uinput device failed, aborting![/CODE]

How to solve this?

Antti


Hi,

$ sudo modprobe uinput
$ sudo wm2js -c 00:22:4C:8D:FF:F7

Enjoy. :)

---

### Post by Tyr42 on 2011-01-22
lswm
[http://ubuntuforums.org/showthread.php?t=993376]("http://ubuntuforums.org/showthread.php?t=993376")

---

### Post by antti64 on 2011-01-22
Sorry, doesn't work for me:

```
sudo modprobe uinput
sudo ./wm2js -c 00:22:4C:8D:FF:F7
Searching Wiimotes ; press 1+2 or the red SYNC button...
Connection established! 0x7fff47d43920
Warning: Unable to open uinput device ; hint: 'modprobe uinput' ?!
Error: Registering the uinput device failed, aborting!

```

wminput and wmgui works fine.

Antti

---

### Post by antti64 on 2011-01-22
Another issue came to my mind. How can I receive Z-acceleration from Wiimote? 

Configuration file only has X & Y. I tried Plugin.acc.Z, but it is unknown for wminput. Where are source codes of the cwiid located under Ubuntu?

```
more /etc/cwiid/wminput/acc_ptr
#acc_ptr

include buttons

Plugin.acc.X	= REL_X
Plugin.acc.X_Scale = 1.2
Plugin.acc.Y	= REL_Y
Plugin.acc.Y_Scale = 0.8
```

---

### Post by ripps818 on 2011-06-07
> **antti64 said:**
> Sorry, doesn't work for me:

```
sudo modprobe uinput
sudo ./wm2js -c 00:22:4C:8D:FF:F7
Searching Wiimotes ; press 1+2 or the red SYNC button...
Connection established! 0x7fff47d43920
Warning: Unable to open uinput device ; hint: 'modprobe uinput' ?!
Error: Registering the uinput device failed, aborting!

```

wminput and wmgui works fine.

Antti

Had the same problem. It seems to be looking for uniput in the wrong place, try this:
```
sudo ln -s /dev/uniput /dev/input/uninput

```

---

### Post by Zvlwab on 2011-09-26
I'd like to use a wii mote + nunchuk as a controller for Mupen64. I'm using cwiid.

This is my config file:
```
# Wiimote
Wiimote.Up = BTN_0
Wiimote.Down = BTN_1
Wiimote.Left = BTN_2
Wiimote.Right = BTN_3
Wiimote.A = BTN_A
Wiimote.B = BTN_B
Wiimote.Minus = BTN_SELECT
Wiimote.Plus = BTN_START
Wiimote.Home = BTN_MODE
Wiimote.1 = BTN_X
Wiimote.2 = BTN_Y

# Nunchuk Buttons
Nunchuk.C = BTN_C
Nunchuk.Z = BTN_Z

# Nunchuk Axes
Nunchuk.Stick.X = ABS_X
Nunchuk.Stick.Y = -ABS_Y
```Everything works fine, except that the  nunchuk's stick gives a too low input so that I'm unable to run in  several games. I googled it, but I was unable to find any good answers.
Also I tried this:
```

Nunchuk.Stick.X_Scale = 2.0
Nunchuk.Stick.Y_Scale = 3.0
```But it just gives some errors when trying to connect

Could anyone tell me how to fix this?

Also when trying wm2js I get the same error as Antti64

---

### Post by Claritux on 2011-10-05
Hi again!
It's been a while since I used the wm2js driver, and now I can't seem to get it to work again! :S I am perfectly able to connect to the wiimote and I can calibrate the Nunchuk with jscal without problems, but Mupen won't react to any joystick/button presses while connected. (Yes, I am using the scaled version) Either something has changed in later Ubuntu releases or I've forgotten something.

---

### Post by arrenlex on 2011-12-05
> **akshov said:**
> Hi again!
It's been a while since I used the wm2js driver, and now I can't seem to get it to work again! :S I am perfectly able to connect to the wiimote and I can calibrate the Nunchuk with jscal without problems, but Mupen won't react to any joystick/button presses while connected. (Yes, I am using the scaled version) Either something has changed in later Ubuntu releases or I've forgotten something.

Hey,

Sorry I didn't see this sooner; it has stopped sending me notifications.

I actually tried playing Mupen again after a long hiatus and discovered this problem independently. Everything on the joystick side looks fine but mupen64plus simply doesn't pick it up.

I tried the newest build of mupen64plus, but unfortunately they've decided to drop the GUI so these days it is pretty much unusable. I mucked about with joystick config files but wasn't able to get anything to register.

I am not sure where to start debugging this -- probably on the mupen side, but then I'd have to dig through mupen64plus code and compile everything. I don't have the inclination to do that right now.

Sorry! :(

---

