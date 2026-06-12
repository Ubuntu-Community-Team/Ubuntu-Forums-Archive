---
title: "Configuring and testing sound"
date: 2009-05-16
forum: General Help
---

### Post by 404wanderer on 2009-05-16
Hello all,

I hope you can help. I have an Intel DG45ID motherboard with on-board sound. I am running Jaunty. I have heard that some people have managed to get sound working on this motherboard, but I'm not sure how.

Currently I have no sound from the HDMI or any analogue sockets.

I have tried the following -

Checked syslog for any errors - none stand out
 
ls -l /dev/dsp
crw-rw----+ 1 root audio 14, 3 2009-05-16 19:35 /dev/dsp
ls -al /dev/audio
crw-rw----+ 1 root audio 14, 4 2009-05-16 19:35 /dev/audio
ls -al /dev/mixer
crw-rw----+ 1 root audio 14, 0 2009-05-16 19:35 /dev/mixer
fuser /dev/dsp

cat /dev/urandom > /dev/dsp (no errors and no sound output)
^C

alsamixer (set everything to 100)



Can anyone give me any advice as to how to find out which sound driver is in use, any how I can test it or configure it further?

Any help appreciated.

wanderer

---

### Post by 404wanderer on 2009-05-16
Just a bit more info - 

aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: STAC92xx Digital [STAC92xx Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
cat /dev/urandom |aplay -c 2
Playing raw data 'stdin' : Unsigned 8 bit, Rate 8000 Hz, Stereo

( and in the words of Simon and Garfunkle, the sound of silence.....)

---

### Post by rongweiss on 2009-05-22
I am brand new with Ubuntu. I am builiding a MythTV box using the DG45ID MB. First I installed Jaunty without MythTV, and was able to get sound to work over HDMI by going to the Sound Preferences app. Then I wiped and reloaded with Mythbuntu 9.04, and I can't find Sound Preferences. No sound over HDMI. I'm thinking of reloading Ubuntu, then putting MythTV on top of that, but I'm not sure I have the expertise to do that.
Does anyone have the answer how to send audio over HDMI with Mythbuntu Jaunty 9.04? Please answer in noob-speak. Thanks!

---

### Post by rongweiss on 2009-05-22
One more thing. Unlike 404wanderer above, I can get sound from the front panel audio jack with headphones. So sound does work. It's just not coming over the HDMI.

---

### Post by Junkieman on 2009-05-23
Hello all, I have this same board, and my *analogue* sound worked fine on Jaunty (I went back to 8.10 to get my 3G working again). Note that I did upgrade from 8.10, so it wasn't a clean Jaunty install.

I don't have a HDMI cable and can't test that side of things. One thing about this board's sound, is that the volume control isn't linear, ie 100% master volume is loud, 75% is barely audible and anything below that is silence, so make sure your master volume is up. Also check your PCM volume in the volume Preferences ;)

Wish I had more in the way of help, my Ubuntu sound experience is very limited :p

---

### Post by 404wanderer on 2010-01-18
Seems to be fixed in Koala.

Thanks for all the responses.

---

