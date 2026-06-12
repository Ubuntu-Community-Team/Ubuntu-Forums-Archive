---
title: "How getting the Hercules DJ Console to work?"
date: 2006-06-27
forum: Desktop Environments
---

### Post by tenzin on 2006-06-27
Hi threre,

I newly got the "Hercules Dj console" at my home...now it works with windows...


[http://www.hercules.com/showpage.php?swcty=UK&p=127&b=0&f=0&PHPSESSID=c238a2473a77ae22fd179359d05d8902]("http://www.hercules.com/showpage.php?swcty=UK&p=127&b=0&f=0&PHPSESSID=c238a2473a77ae22fd179359d05d8902")


but how do I get that thing to work on my ubuntu dapper?


thx for some hints & answers :)

---

### Post by tenzin on 2006-07-01
nobody uses the console for djing?

I know she is a little bit "amateur" but, hey...she is nice and small....


so I am shure that few of you guys have this working, comeon :)



[Edit: The console basicly works great! I can use the "mouse" on the dj console but the only thing is how to "programm" the buttons?]

---

### Post by Mister Mamat on 2006-10-15
Hey,

I'm searching for a while to use dj console with ubuntu.
I found some things.

Sound card seems to work (headphone output, i don't know), i've installed packages to drive the controller as joystick (but usb joystick) :
joystick
jscalibrator
libjsw2

joystick seems to work as well, jscalibrator recognise it

but i want to use mixxx but it accepts only midi device,
the config file is easy to understand and change but how to use usb joystick as midi one?

cheers
Mat

---

### Post by s3lf on 2006-11-18
Did you try mixxx 1.5 beta? There seems to be a special hercules DJ console integration. I currently decide to buy one, too. It would be nice to know if all works :) 

Alex

---

### Post by Sebastral on 2007-02-20
[DJPlay](http://djplay.sourceforge.net/) live DJing application for Linux:

# Santa's been here! DJ Console access is now a separate lib
# Native support for the Hercules DJ Console through libusb
# Now supports the joystick on the DJ Console
# DJ Console controls can be reassigned by config files

---

### Post by Adri2000 on 2007-06-08
libdjconsole (available since feisty), library used by DJPlay, supports Hercules DJ Console MK I and MK II.
So if you are using feisty (or gutsy), just sudo apt-get install djplay :)

---

### Post by Sebastral on 2007-06-13
Ok, _[so I have the dj console working with alsa (v1.0.13)?](http://ubuntuforums.org/showthread.php?p=2835155#post2835155)_

I now have arrived at the next.

$: jackd -d alsa
[INDENT]jackd 0.102.20
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details

JACK compiled with System V SHM support.
loading driver ..
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
configuring for 48000Hz, period = 1024 frames, buffer = 2 periods
ALSA: final selected sample format for capture: 16bit little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 16bit little-endian
ALSA: use 2 periods for playback[/INDENT]
$: qjackctl
says in settings;
hw:0 = NVIDIA Nforce2
hw:0,0 = NVIDIA Nforce2
hw:2 = DJ Console WS
hw:2,0 = USB Audio

$: djplay

[INDENT]    Hercules Console found at libusb:003:002 (0x06f8-0xb000)
    Successfully attached DJ Console
    Port alsa_pcm:capture_1
    Port alsa_pcm:capture_2
    Port alsa_pcmlayback_1
    Port alsa_pcmlayback_2
    Port alsa_pcmlayback_3
    Port alsa_pcmlayback_4
    Port alsa_pcmlayback_5
    Port alsa_pcmlayback_6
    Audio player cannot su to root
    Audio player cannot su to root[/INDENT]
I beg for some clues on how to set this up ;). Shouldn't jackd load the console as device? I tried;
$: jackd -d alsa --device hw:2
and
$: jackd -d alsa --device hw:2,0
but then djplay can't even pretent it's playing a file (ergo; if I push play it doesn't start playing while with hw:0 it did)

---

