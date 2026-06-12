---
title: "Screen Resolution Change Attempt --Gone Wrong"
date: 2007-04-22
forum: Desktop Environments
---

### Post by topgun553 on 2007-04-22
Alright so this is my fourth time that I have had to reload feisty os onto this computer from changes i have made to xorg.conf to try and change my screen resolution. I have a computer with the following information:

MONITOR: 15.4" WSXGA TFT LCD DISPLAY 1680x1050

VIDEO: 16X PCI-Express NVIDIA Geforce GO 6600 128MB Video

All I have done so far is update the automatic updates and then i turned my restricted driver for nvidia on and then turned on
"Desktop Effects"

Then i tried to edit xorg.conf via
sudo dpkg-reconfigure xserver-xorg -phigh

I selected nvidia then on the following screen

Video modes to be used by X server

I tried to select 1400 x 900 by pressing ctrl which is what i was told to would work
then i think i pressed ctl up or over and it exited terminal

then i ctrl alt backspaced

and it had new nvidia screen but said nautilus failed to start. 

then i restarted and now

I can't see any of the tops of my windows... unless i turn off desktop effects...

I want to eventually have beryl and a screen resolution higher then my current 1024x768 which causes everything to look really strectched on my screen (Around 1400 x 900 ?? )

note: i realize when i install beryl i will have to turn off desktop effects


PLEASE HELP!!! the last 3 attempts has caused me to have to reinstall feisty since i didn't know what  to do to fix it.

---

### Post by dcstar on 2007-04-22
> **topgun553 said:**
> Alright so this is my fourth time that I have had to reload feisty os onto this computer from changes i have made to xorg.conf to try and change my screen resolution. I have a computer with the following information:
.........
PLEASE HELP!!! the last 3 attempts has caused me to have to reinstall feisty since i didn't know what  to do to fix it.

There is no need to "reload" anything if you muck up your xorg.conf file, all you need to do is manually edit it after your system starts.

Do a forum search for the many posts detailing instructions on how to recover from incorrect resolutions or refresh rates or bad xorg.conf settings.

---

