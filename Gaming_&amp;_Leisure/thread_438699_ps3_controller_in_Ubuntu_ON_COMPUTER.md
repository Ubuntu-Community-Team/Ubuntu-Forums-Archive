---
title: "ps3 controller in Ubuntu ON COMPUTER?"
date: 2007-05-10
forum: Gaming &amp; Leisure
---

### Post by AR_Kozz on 2007-05-10
Having got my ps3 (finally!) last week.  Of course I will put a linux distro, probably Edgy, onto it. The walkthroughs are all there on psubuntu.com. But there's something else I'm trying to do: make the controller work on my computer, in Ubuntu. 

I have Dapper and could never get my gameport controllers (a gravis gamepad pro and a Sidewinder) to work as anything other than a 2-axis, 4-button joystick. Which REALLY sucks for games like bzflag and America's Army.  So now I've got this usb six-axis controller, which should work much better than a gameport controller. Dapper even recognizes it and lists it in the Gnome Device Manager. But it doesn't even begin to function, and jscal produces only errors.

Apparently the controller does work under linux installed on the ps3 itself, if I understand what I've read on psubuntu.com correctly. But not on my computer. I figured, there must be a module for it, similar to the xpad module, but much searching has found me nothing.

   Whoever can point me to the solution to getting the sixaxis to work in dapper ON THE COMPUTER not the ps3, I will invoke the gods to make you own all your enemies the next time you play an online game.. 

btw I would post on psubuntu.com, but they never sent me email to finish my registration...

---

### Post by wounded on 2007-05-10
Unfortunately I probably won't offer anything useful to you as I know little about the controller set up of the PS3 (I have no PS3 and am somewhat unsure if I am even understanding your post correctly haha). However, assuming that it uses the same controller port as the PS1 and PS2 you *may* be able to buy an adapter from radio shack or another place (Mine was under ten bucks at Radio Shack). It plugs into a USB port and then you pug in your PS1/2 controllers into it. Mine works perfectly on Linux (PS2 controller) without any configuration. I play NES/SNES/MAME/PS1 games with it easily.

While I think it lets me use the analog sticks on the PS controller I don't know if it will give you the full functionality of the PS3 controller but maybe it will give you some idea to lead you in the right direction.

Aside from their not being a picture, I think this is what I have: [http://www.radioshack.com/sm-usb-adapter-for-playstation-2-controller--pi-2348187.html](http://www.radioshack.com/sm-usb-adapter-for-playstation-2-controller--pi-2348187.html)
EDIT: [http://wiredblogs.typepad.com/gadgets/ps2tousb.jpg](http://wiredblogs.typepad.com/gadgets/ps2tousb.jpg) Mine looks slightly different but it is the same thing.


If that one doesn't work, maybe there is an adapter made specifically for the PS3?

Good luck.

---

### Post by treblesix on 2007-05-12
I bought a PS2 USB controller adaptor.
Needed a driver to get it running in Windoze, but just worked as soon as i plugged it in on Ubuntu ;)

Think i bought it off Ebay

---

### Post by srt4play on 2007-05-14
> If that one doesn't work, maybe there is an adapter made specifically for the PS3?

An adapter is not necessary.  The ps3 controller is wireless, but has a connection similar to some digital cameras for connecting to a usb port to charge the battery.

---

### Post by francisco_athens on 2007-07-08
There has been some experimental success with the sixaxis in GNU/Linux.  There seems to be hope in getting the device to work in bluetooth wireless mode and with motion sensing.

[http://www.pabr.org/sixlinux/sixlinux.en.html](http://www.pabr.org/sixlinux/sixlinux.en.html) 

from that page I was able to get Ubuntu Feisty to "pair up" with sixaxis via usb, but got no further. :(

Hopefully some of this stuff will appear in the kernel updates as the controller gets more popular.  It would be a real boon as this controller is an amazing device. 

> 
Joystick (Sony PLAYSTATION(R)3 Controller) has 28 axes (X, Y, Z, Rz, ...)
and 19 buttons (Trigger, ThumbBtn, ThumbBtn2, ...)

So the joystick seems to provide 28 analog axes &#8212; a lot more than the advertised 6! Remember that nearly all buttons on the controller are actually pressure-sensitive, so they are treated as both a digital button and an analog axis.
 from: [http://ps3.jim.sh/](http://ps3.jim.sh/)

There seem to be more clues about the sixaxis bluetooth behavior in the Apple mailing list:
(Note: Though this refers to OS X, Linux may experience a similar issue)
[http://lists.apple.com/archives/Bluetooth-dev/2007/Jun/msg00006.html](http://lists.apple.com/archives/Bluetooth-dev/2007/Jun/msg00006.html)
> 1. This device does not support the HIDP "Set protocol" command.
   Immediately after the Bluetooth connection is established:
   - Mac OS X sends "Set protocol: Report protocol" (0x71)
   - The device replies with "Unsupported request" (0x03)
   - Mac OS X terminates the connection, possibly because it
     considers "Unsupported request" as a fatal error here.

---

### Post by francisco_athens on 2007-08-25
I'm happy to report that the sixaxis works in **Ubuntu Gutsy 7.10** as a *bluetooth* device, tho functionality is not quite complete.

**JSCalibrator** shows analog sensitivity only for the two analog sticks, but the remaining buttons seem only to work in a digital (on off) fashion, even though they have pressure sensitivity capability.

The motion sensors and accelerometers still seem unavailable too.

The **zsnes** in the current Gutsy (tribe 4 at time of testing) seems to work well with the sixaxis in BT mode but cannot utilize the analog sticks, only the dpad and buttons.  But that certainly makes it functional and a lot of fun!

After using the the **sixpair** program (with the sixaxis connected via usb) and starting the **hidd** server once, the sixaxis should work with the usb disconnected and after pressing the PS button on the controller, but to use it again, one must delete (as root) the /var/lib/bluetooth/<BT host MAC address>/hidd file before the sixaxis can be paired again. This seems a bit kludgey.

the sixpair and hidd programs must be run as root (sudo) and this seems a bit unsafe and a inconvenience for a user.  

The sixaxis may not be the most daring controller but is the most evolved consumer-level gaming controller yet and kudos to Sony for using established standards such as BT and usb instead of going their prior proprietary route!!!

---

### Post by qirtaiba on 2008-03-23
I am running Gutsy with the stock kernel 2.6.22-14.  I have the sixaxis controllers from the PS3 and am trying to use them either as USB or bluetooth joysticks.  There is ample documentation about this which I have followed.  However although the controllers are recognised by the kernel and respond to the device file /dev/input/js0, none of the buttons work.

For example: I have run jsconfigurator, which should show me the buttons that I am pressing on the controller as I press them, but it doesn't. Similarly there is a program called js2key which ought to respond to a button press but won't (see [http://ubuntuforums.org/archive/index.php/t-646564.html](http://ubuntuforums.org/archive/index.php/t-646564.html)).  Finally when I run jstest --event which should show button presses as I make them, it doesn't.

Having said that, when I run Planet Penguin Racer, TuX spirals around like a loon, so obviously it thinks that I am pressing something even though I'm not, but nothing that I do press makes any difference.

Have searched the mailing list and Web archives to no avail.  Can anyone suggest what might be going on here?  Needless to say the controllers work on the PS3.

TIA

---

### Post by acoustibop on 2008-03-23
I notice the last 2 posters are using jscalibrator.  Try removing this, including configuration files, and reboot.

jscalibrator very frequently reports buttons or directional controllers as working (most often directional controllers) while actually disabling them for other applications.

---

### Post by ricanelite on 2008-03-23
okay, i have a question. How do I get my PS3 controller working on ubuntu linux 7.10 on my ps3? Just installed linux on my ps3. Got some roms of nes games they play perfect. Just dont know where to start on getting my ps3 controller working in linux

---

### Post by Gliitch on 2008-06-04
yay first post!! :D


Here's the guide I followed for wireless configuration.

[https://help.ubuntu.com/community/Sixaxis](https://help.ubuntu.com/community/Sixaxis)


Where it says "Driver Setup" at the bottom, i just ignored it. It should be the same for the ubuntu ps3 version ive only done it on the pc.


I hope this helps anyone :)

Gliitch ^^
*EDIT* - when extracting  xserver-xorg-input-joystick_1.3.1.orig it has a different directory name, so just copy and paste the xserver part and it will let you go into the directory.

using the pad via usb also works, just need to run ./sixpair as root. also whilst  plugged in it does charge just incase anyone asks :P (some forums say it doesnt, meh.. oh well)

---

### Post by Akegata on 2008-06-10
This is driving me insane.
I've succesfully paired my controller to a PC running Ubuntu 8.04, but it only works the first time. When I disconnect the controller, or reboot the computer or whatever, it stops working.
The controller gets discovered, and /dev/input/js0 is created, but nothing happens when I press the buttons.

The hcidump stops at "2008-06-10 23:29:15.148389 > ACL data: handle 7 flags 0x02 dlen 5
    L2CAP(d): cid 0x0040 len 1 [psm 17]
      HIDP: Handshake: Successful"

I can't get anything to happen from here on, I've tried with another controller, same thing. Tried to patch the bluez-utils package, same problem.
Does anyone have any idea what could be wrong?

---

### Post by lernatix on 2008-10-04
This is a _COMPLETE_ guess.

Sometimes I have trouble using the sixaxis on the PC too.

Have you tried pressing the PS button?  Seems to fix it on XP.

---

### Post by Gliitch on 2008-10-29
[https://help.ubuntu.com/community/Sixaxis](https://help.ubuntu.com/community/Sixaxis)

Try the above link, step by step. I had the problem for ages too, - well it refused to work, so i got rid of the all the config files, did it again and it worked. 

I paired it with an emulator, (gens in my case) and it came up with a pop up saying "authorise for this session only or trust." So i set it to trust and i havnt had problems since.

---

### Post by DigitalWolf333 on 2009-07-16
i know this is a very old post but i tried this and got this error

following the 'using sixaxis  as pointer' tutorial and getting to putting in 'sudo make install'

```

Making install in src
make[1]: Entering directory `/home/digitalwolf/input-joystick/xf86-input-joystick-1.3.1/src'
/bin/bash ../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I..     -g -O2 -I/usr/include/xorg -I/usr/include/pixman-1    -I../src -MT jstk.lo -MD -MP -MF .deps/jstk.Tpo -c -o jstk.lo jstk.c
 gcc -DHAVE_CONFIG_H -I. -I.. -g -O2 -I/usr/include/xorg -I/usr/include/pixman-1 -I../src -MT jstk.lo -MD -MP -MF .deps/jstk.Tpo -c jstk.c  -fPIC -DPIC -o .libs/jstk.o
jstk.c:30:25: error: xf86Version.h: No such file or directory
jstk.c: In function 'jstkDeviceControlProc':
jstk.c:354: warning: passing argument 3 of 'InitValuatorClassDeviceStruct' makes integer from pointer without a cast
jstk.c:354: error: too many arguments to function 'InitValuatorClassDeviceStruct'
make[1]: *** [jstk.lo] Error 1
make[1]: Leaving directory `/home/digitalwolf/input-joystick/xf86-input-joystick-1.3.1/src'
make: *** [install-recursive] Error 1


```

---

