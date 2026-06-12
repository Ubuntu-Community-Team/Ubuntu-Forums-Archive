---
title: "I can hear my PC through the speakers"
date: 2012-10-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by resander on 2012-10-24
I bought a Vostro 260 desktop tower from Dell UK a month ago. It came with Windows 7 preinstalled and I made it dual-boot by adding Ubuntu 12.04 LTS. That works fine.

I normally use the speakers at low-moderate levels but a couple of days ago I increased the volume to listen to music while doing other things in the room. Forgot to reduce the volume.

I could then hear sounds from the speakers when operating the PC:

-  hum when moving the mouse - hum stops when mouse stops
-  hum and 'interference' noise when using the mouse to highlight text
-  no hum and interference noise when using the keyboard, but can hear a keyboard click when pressing a key and machinegun-like effect when pressing key to repeat
-  disk access sound (access arm/mechanism moving) when viewing a large file, e.g. a pdf manual. Disk access sound is clearly audible when scrolling but also when using the arrow keys (then keyclick is present too).


I am using USB speakers (powered via the USB cable) and a USB mouse. There are no PS2 connectors at the back of the computer.

Q1. is anyone else experiencing this?

Q2. should this be or is it likely to be something 'electrically' wrong with the PC?

Q3. what can I do to pinpoint the cause and understand this a bit better?   
    

Hoping for advice...

Ken

---

### Post by Scott Goodgame on 2012-10-24
That is usually RFI (interference) try tying up your speaker cables to as short as possible.

---

### Post by resander on 2012-10-25
Thanks Scott,

1. I first tried placing the speakers as far away as possible from the PC. That did not make any difference. I then shortened the straight run of speaker cables by coiling them up. No difference, or maybe the coiled cable picked up more noise per unit of length since it is nearer the PC.

2. tried with headphones/headset. Quiet like a church mouse. No noise at all.

3. then tried the speakers on another PC (Compac Evo D310) dual-booted with Windows XP and Ubuntu 12.04.
No noise from Windows. Some noise from Ubuntu 12.04. No noise at all from head phones.

There is noise from Dell Vostro for Windows and Ubuntu, but it is louder for Ubuntu 12.04.

Maybe the speakers are affected by noise from the PC, but a PC should not emit stray signals that can be picked up like this outside the PC. What does interference compliancy regulations have to say?

Ken

---

### Post by Grenage on 2012-10-25
It's not that uncommon; devices can emit noise, but they else have to accept any noise that comes their way (I believe).  My work colleague doesn't use a case, and when his PC is in use, his Father can't pick up BBC R4.

Some speakers are, to be frank, just awful at picking up surrounding interference.

---

### Post by resander on 2012-10-25
Here are some paragraphs copied from thread 'Can hear mouse and moving windows in my speakers' at [www.tomshardware.co.uk](www.tomshardware.co.uk)

Paragraph A.
In this thread imkey wrote :

This is a design flaw either in the motherboard or back/front panel header which shorts usb ground to audio ground.

and InvalidError expands this further:
USB ground is usually tied to case ground (either directly or through motherboard headers which are themselves tied to case ground through the IO plate and studs) which is in turn connected to electrical ground which the amplifier is likely connected to as well.

Even if you put some sort of impedance between analog and digital ground on the motherboard, the two get shorted out through electrical ground at the amplifier's end which closes the ground loop. The amplifier whine in this case would be the voltage difference between analog ground, digital/case ground and amplifier ground.

If you want to reduce ground noise in such a situation, the first thing to do/try is connect all equipments to a single common grounding point such as a power bar or even a #14 gauge wire directly connecting the amplifier's case to the PC's case. Good amplifiers often have a ground wire binding post for such uses on their chassis. On the PC's end, crimp/solder a fork or ring style connector and screw it under one of the PSU's screws.


Paragraph B.
JMV103 in the same thread suggests: adjust the sound setting level on the PC to max and change the sound knob of the speakers to the smallest possible setting that gives desired volume...

Paragraph C.
Pixelpusher6 proposes using a hub...

 Ok, I had this exact same issue when using my CM Storm 5.1 Surround Headset plugging directly into my Creative X-Fi PCI card's analog outputs (using the other set of cables and only plugging into 1 USB port for power) and my Logitech G500 Wired Mouse. If there was no sound being played, whenever I moved my mouse or clicked a button I would hear a interference sound or buzzing. I figured it must be related to interference between the two devices and like another poster commented probably related to the ground. I did find this kind of strange because the headset was only using the USB port for power, and trying different combinations of ports did not help. Anyway what I did was I used a powered 4 port USB hub that also plugs into a wall outlet and I plugged the USB connector from the headset into this hub. Completely fixed the problem - crystal clear sound now. I'll have to do some more testing and reverse the connections i.e. plugging the mouse into the USB hub and the headset USB into the back of the computer. If anyone tries this method I think it is necessary to use a "powered" USB hub that receives power from the wall instead of one that only gets power over the USB bus. I got mine from Best Buy for $20-25 and it's a Belkin. Good Luck. 




The speakers get the power from the PC USB socket and receives the sound from the light-green (analogue?) PC output port. 

However, if I power the speakers from the USB port of another computer (Lenovo laptop) there is no noise at all - exactly like when using a headset. This proves this is a hardware problem, but it does not prove what is causing it. It may be caused by audio ground and usb ground inbalance on the PC (see paragraph A above) or poor speakers. They were bought at Argos in UK. Unknown brand, which by itself does not imply they are inferior.

I tried adjusting the sound levels and speaker volume as suggested in B. That worked very well.
However,

Q4.  The PC sound settings for Ubuntu can be set a value between 0 and 150%. What is the effect of setting the level to a value above 100%. Distortion? What is the max setting? I don't have any good quality recordings to try.

Feedback welcome.
Ken

---

