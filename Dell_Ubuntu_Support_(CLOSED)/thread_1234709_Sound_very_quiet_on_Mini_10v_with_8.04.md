---
title: "Sound very quiet on Mini 10v with 8.04"
date: 2009-08-08
forum: Dell Ubuntu Support (CLOSED)
---

### Post by MartynT on 2009-08-08
I have a mini 10v running 8.04 pretty much how it was delivered (I've applied all updates and installed a few things - skype etc.)

The problem is the sound is very quiet.  I pretty much have to hold the underside of the keyboard to my ear to hear utube or skype.

With earbuds plugged into the headphone jack it isn't as bad (on 100%) but is not loud by any means.

If I go to System->Preferences->Sound I can change the playback for "Sound Events", "Music and Movies" and "Audio Conferencing".  

The options are Autodetect (the default), "ALC272 Analog", "Bluetooth", "ALSA", "OSS", "Pulse Audio".

If I try the test button with each of these I get a quiet tone for all except OSS which is MUCH louder (actually Bluetooth just errors but I have no plan to use BT).

If I select OSS and go back to skype or utube (firefox) the sound level is the same as it always was, i.e. not loud like the OSS test button.

Having done all this, retesting the OSS button just gives a "could not open device.  Being used by another application." Error.  Closing FF might fix this, but I want to finish typing this before I do ;-)

This is the card in the 10v

```
:~$ sudo lspci | grep -i audio
[sudo] password for martyn: 
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
```

---

### Post by karumudi7 on 2009-08-08
Right click on Sound icon in tray(Top Right) click open volume control increase all bars to up..
The same prob came 4 me in Latitude when I increased now the sound is coming normally like in windows..
:guitar:

---

### Post by bri5569 on 2009-08-17
I had the same problem - but after downloading Dell's iso of 9.04 my volume is pumping. Everything else works out of the box as well.

---

### Post by MartynT on 2009-08-23
Thanks Bri, that's good to know.  Unfortunately the 10v's microphone doesn't work in 9.04 and I'm told it's not going to be fixed until 9.10.

Oh well.  I do have a plug in microphone.  Maybe that'll work.

karumudi - of course my volume is set to maximum !

---

### Post by MartynT on 2009-08-23
> **karumudi7 said:**
> Right click on Sound icon in tray(Top Right) click open volume control increase all bars to up..


Hi Karumundi,

I didn't read your reply properly !  I assumed that the left click volume slider was all there was to it.  When I opened the Volume Control I saw that PCM (which is presumably a music/speech channel) was at 2/3rds.  Setting that to 100% solved my problem.

Thanks, and apologies for my previous reply.

I suspect that the default setting for PCM was increased in 9.04 and hence why the upgrade solved the problem for bri.

Thanks again.

---

