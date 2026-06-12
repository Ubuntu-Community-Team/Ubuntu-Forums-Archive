---
title: "Game pads, Joypads and Joysticks in Ubuntu"
date: 2010-09-27
forum: Gaming &amp; Leisure
---

### Post by gdbutcher on 2010-09-27
Hi I wanted to start this thread to gather some accurate and up to date information for Ubuntu users who want to use Gamepads/Joypads/Joysticks in their games. 

There seems to be a lot of unanswered questions on the forums and most of the webpages on these issues tend to be for earlier versions of Ubuntu. Some of the packages mentioned seem to be obsolete.

I was thinking we could use this thread to find out as of Ubuntu 10.04:

1. What support is there for Gamepads/Joypads/Joysticks in Ubuntu 10.04 and above?

2. What devices work well and what can you recomend to other Ubuntu Users?

3. What applications currently support Gamepads/Joypads/Joysticks and what would you like to see?

Please do not turn this into Keyboard & Mouse Vs Gamepads/Joypads/Joysticks flame fest. This is a thread designed to help fellow users not as a criticism of one device over another.

---

### Post by wilbuzz2 on 2010-09-27
ubuntu 10.04 doesnt have a lot of support for gamepads i think a xbox  360 controller works with a usb cable.the games so far that i know that have gamepad support are maniadrive,a few more that have gone out my head like gl-117 flight gear.i would like to see assault cube smoki guns and urban terror to have support:popcorn:

---

### Post by gdbutcher on 2010-09-27
I have a GreenAsia USB PS2 Style joypad and an XBOX 360 PC Wired Joypad, both work well in Snes9x-GTK and Mupen64.

I haven't been able to get them to work in Skulltag running Doom 2, Ultimate Doom, Plutonia, or Tnt. The original games do have Joystick/Joypad support but they can't find seem to find the joypads when run through Skulltag.

I would love to use a Joypad in native games such as Return to Castle Wolfenstein or Doom 3. I find playing FPS games using the keyboard and mousepad on my laptop pretty uncomfortable and not much fun. 

Can anyone recommend an application like Xpadder (on Windows) that allows the user to allocate keyboard keys and mouse movements to the Joypad?

---

### Post by R33D3M33R on 2010-09-27
I have Saitek Strike2 USB gamepad and it works great out of the box on 10.04. I calibrated it through KDE's control center.

---

### Post by dfreer on 2010-09-27
Most controllers use a standard USB HID driver, which means you generally do not need to install a driver, it's just plug and play. I know my logitech chillstream DOES need a driver, it's one of the few.

And see my sig about installing jscalibrator. Try the controller first to see if it even needs to be calibrated, if it does look for an alternative to jscalibrator.

---

### Post by fallenshadow on 2010-09-28
I have 2 gamepads at the moment:

Alienware:
[http://www.amazon.com/Playstation-PC-Alienware-Gamepad-Controller-2/dp/B000HEV7Q0/ref=pd_rhf_shvl_2](http://www.amazon.com/Playstation-PC-Alienware-Gamepad-Controller-2/dp/B000HEV7Q0/ref=pd_rhf_shvl_2)

Gamestop 1000GS:
[http://www.gamestop.no/game.asp?id=230](http://www.gamestop.no/game.asp?id=230)

Both work perfectly under Ubuntu 10.04.

---

### Post by mister_playboy on 2010-09-29
I use a PS2 controller with an USB adapter. :guitar:

---

### Post by Mike_30 on 2010-10-03
> **mister_playboy said:**
> I use a PS2 controller with an USB adapter. :guitar:
Really?Did you need to install anything? or does ubuntu see it automatically?

---

### Post by rizzeh on 2010-10-04
I have a Xbox 1 controller with soldered USB plug, Ubuntu picked those up automatically.
some info [here]("http://www.velocityreviews.com/forums/t482-guide-xbox-controller-to-usb-adapter.html")

---

### Post by mister_playboy on 2010-10-07
> **Mike_30 said:**
> Really?Did you need to install anything? or does ubuntu see it automatically?

It works automatically, identifying itself as a PS3 controller via the USB ID... even Windows 2000 works with it automatically... also works with my PS3.

I bought it at a WalMart, but I haven't seen anything similar in a store recently... maybe look on eBay?

It is called Pelican PS2 to PS3 Adaptor PL-6338.  It's pretty old, there might be a newer version.

---

### Post by gdbutcher on 2010-10-24
Thanks to everyone for the contributions, just to let everyone know that I found qjoypad 4.1.0 which works fairly well with eduke and skulltag. 

You will have to map your joypad buttons to keys before it works. 

It works in Ubuntu 10.10 64. here's the code if you want to install it:

```
sudo apt-get install build-essential
sudo apt-get install libxtst-dev
sudo apt-get install libqt4-dev
wget http://downloads.sourceforge.net/qjoypad/qjoypad-4.1.0.tar.gz
tar -xzvf qjoypad-4.1.0.tar.gz
cd qjoypad-4.1.0/src
 ./config
make
sudo make install
```

---

### Post by milok on 2010-11-20
Okay, so I'm having quite the opposite problem as user gdbutcher.  My joystick seems to control my mouse cursor.  The buttons do nothing. The left analog control controls the mouse position (holding the stick to the left puts the cursor on the left side of the screen, holding the stick half-way to the left puts the cursor half-way to the left).

Although it doesn't matter which USB joypad I plug in. I've got the Macally below, I've got a couple ps2->usb and GameCube->usb adapters, a non-analog joystick (which doesn't do anything to the mouse cursor), and another couple analog joypads.  They all used to work in 9.X, but the upgrade to 10.X seems to have broken them.  Installing 10.X from scratch didn't help either.

Any ideas?

The relevant output from /proc/bus/input/devices is:

I: Bus=0003 Vendor=2222 Product=4010 Version=0100
N: Name="Macally  Macally iShock"
P: Phys=usb-0000:00:13.5-3.1/input0
S: Sysfs=/devices/pci0000:00/0000:00:13.5/usb1/1-3/1-3.1/1-3.1:1.0/input/input5
U: Uniq=
H: Handlers=event5 
B: EV=1b
B: KEY=f ffff0000 0 0 0 0 0 0 0 0 0
B: ABS=63
B: MSC=10

---

### Post by weasel fierce on 2010-11-23
I have a logitech USB pad, as well as an adapter for a PS2 controller, and both worked without a hitch. 
For games that use the keyboard, rejoystick is a really easy tool to set it up. Works wonders for Doom and similar :)

---

### Post by zzarko on 2010-12-22
> **milok said:**
> My joystick seems to control my mouse cursor.
I have the same problem and I don't know how to turn this off. xorg.conf is clean, I installed qjoypad and tried to re-assign something, and I only got new mappings, without old ones being turned off.

If someone could at least point me where to search, I'll be grateful...

EDIT: I found something called /usr/share/X11/xorg.conf.d/50-joystick.conf with this content:
```
Section "InputClass"
        Identifier "joystick catchall"
        MatchIsJoystick "on"
        MatchDevicePath "/dev/input/event*"
        Driver "joystick"
EndSection
```Maybe this is responsible for automatic joypad mouse emulation?

EDIT2: Yep... Added those to above file:
```
    Option "StartKeysEnabled" "False"
    Option "StartMouseEnabled" "False"
```and my problems were gone... :) I'm glad I answered myself :)

---

### Post by Cee64E on 2011-01-22
I'm really interested in this as well.  I have a MS Sidewinder Force Feedback 2 stick (old as dirt but I love it) that I can't figure out how to use.  I'm new to linux and Ubuntu in general, I have very little knowledge of how this is all supposed to work.  Can someone tell me how to activate joystick support?  I'm using Ubuntu 10.10 dual booted with WinXP Pro.

---

### Post by Advice Pro on 2011-04-08
> **gdbutcher said:**
> 
```
build-essential

```

What's this for?

Please answer my question at:

[Help with requirements & install for QJoyPad 4.1.0!](http://ubuntuforums.org/showthread.php?p=10652662#post10652662)

---

