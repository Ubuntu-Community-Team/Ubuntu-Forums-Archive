---
title: "Mic and wireless"
date: 2008-05-22
forum: Dell Ubuntu Support (CLOSED)
---

### Post by xtracool_protik on 2008-05-22
Hello guys it seems that microphone in my XPS1530 is not functioning in ubuntu hardy 8.04 can anybody help me. I haven't even tried changing the device from sound and multimedia because I don't know what to do
Thanks for help in advance Even it seems that wireless is not working does anybody know anyhting about it

---

### Post by barnex on 2008-05-22
I have had some trouble getting my mic to work on a macbook, one of the necessary steps in my case was playing around with the settings in gnome-volume-manager. 

First I set all tracks visible (via Edit > Preferences), then I played around with all the settings, e.g.: Switches / Mic as output has to be off, Options / Input Source is on 'Mic', and in 'Recording' I have Capture and Digital on maximum volume and unmuted. Of course your dell may need different settings.

Then, in sound-preferences, I set all the input devices in 'ALSA'. This was necessary to get e.g. Skype working.

I hope this helps, your mileage may vary ;)

---

### Post by xtracool_protik on 2008-08-30
Well guys after installing gnome alsa mixer u can have option of all the mics - i/p devices so just install it and give it a try worked for me
Well wireless is in progress let's see wat happens

---

### Post by xtracool_protik on 2008-09-18
Ya and for wireless in 8.04 there is absolutely no need of external drivers while for broadcom(dell) Network devices u may need ndiswrapper and system->administration->hardware

---

