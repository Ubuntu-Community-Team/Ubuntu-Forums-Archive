---
title: "Installing new sound card (audigy 2)"
date: 2005-12-17
forum: General Help
---

### Post by Ryanmt on 2005-12-17
Hi, i have just installed my new sound card but its not working as planned. i had to disable the onboard one to make it work however in alsamixer the chip is still "SigmaTel StAC9750,51" 

How do i install the driver for the audigy 2 so i can use 5.1 surround?

Thanks
Ryan

---

### Post by amohanty on 2005-12-17
In System->Preferences->Multimedai Systems Selector
I think in the File menu theres an option called Select Device (not on my box right now). There select the audigy 2 and you should be good to go.

I have the Audigy2 ZS and 5.1 works out of the box. Take a look at what I can use in my volume control:
[http://www.ubuntuforums.org/showpost.php?p=551246&postcount=7](http://www.ubuntuforums.org/showpost.php?p=551246&postcount=7)

HTH
AM

---

### Post by Ryanmt on 2005-12-17
There isnt anything like that in multimedia systems selector. There is in sound but i only have one soundcard to choose from "CA0106"

---

### Post by amohanty on 2005-12-17
Sorry I was wrong, goto:
System->Preferences->Sound

Screenshot attached.

[ATTACH]4609[/ATTACH]

---

### Post by Ryanmt on 2005-12-17
I dont have an audigy 2 there, just CA0106. lspci shows up the audigy LS. Ive tried alsamixer -c1 etc upto 8 but i aways get "function snd_ctrl_open failed for hw:1 No such file or directory"

---

### Post by amohanty on 2005-12-18
I think the "CA0106" is associated with the SB Live! 24 bit cards or the Audigy 2 LS/HD EAX.
Is that the card you have?

If you select that, does sound work then?

---

### Post by Ryanmt on 2005-12-18
yes it does, however i cant get 5.1 surround working and im 110% sure ive turned up ALL the volume controls in alsamixer, however the speaker test does work in 5.1 ..

---

### Post by amohanty on 2005-12-18
> however the speaker test does work in 5.1 ..

If this works, how are you determining that 5.1 does not work? Also play with the various settings in volume control. I have found that I can use the following and can hear the 5.1 working by changing some values:

Master
Headphone
Front
Surround
Center
LFE
CD
PC Speaker

By decoupling front and surround (click on the link icon at the bottom) and moving the scales, you can hear output moving across speakers.

HTH

---

### Post by Ryanmt on 2005-12-20
ive played with the volume control settings for hours and hours nothing :(

---

### Post by amohanty on 2005-12-20
Does this work:

> speaker-test -c6 -D plug:surround51

Is this what you were referring to when you said speakertest works?

---

### Post by DJStillman on 2005-12-20
I am using an Audigy 2 ZS, and it autodetected fine, but the sound is really crappy.  My board also had onboard sound disabled in BIOS.  There are probably better drivers hiding somewhere...

Let us know when you get the 5.1 figured out.  I am upgrading to one, and would like to have that solution ready...

---

### Post by Ryanmt on 2005-12-20
yep thats the command, ive even installed kmixer (i think thats what its called) and tried all the levels in that.. nothin :(

---

### Post by amohanty on 2005-12-20
> I am using an Audigy 2 ZS, and it autodetected fine, but the sound is really crappy.

Thats surprising actually. Its working great for me. 

Ryanmt: Try disabling the SPDIF and Optical outputs (Ithink they are the ones wiht IE... or OE... in front) if they are on. BTW how are you determining that 5.1 is not working?

AM

---

### Post by DJStillman on 2005-12-20
[QUOTE=amohanty]Thats surprising actually. Its working great for me. 

Ryanmt: Try disabling the SPDIF and Optical outputs (Ithink they are the ones wiht IE... or OE... in front) if they are on. BTW how are you determining that 5.1 is not working?

AM[/QUOTE]
When I say crappy, the quality is good but the volume controls suck.  I have to max out my master volume to be able to hear webcasts that play perfectly fine on a Windows Pc...  Is there a better driver than the default?

---

### Post by amohanty on 2005-12-20
> When I say crappy, the quality is good but the volume controls suck.

What kind of speakers are you using. On my Logitech X530, it sounds pretty good even on moderate volumes. I agree that the volume controls are not as sensitive as I would like them to be - quite frankly they suck, so I turn it on to max and manage sound via the speaker's volume control. I would sure like the range to be better.

---

