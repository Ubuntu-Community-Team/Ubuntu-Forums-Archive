---
title: "wich ICH6 device?"
date: 2007-12-02
forum: Dell  Ubuntu Support
---

### Post by ivago on 2007-12-02
Hello, 

I have a ICH6 audiochip in my Dell Optiplex GX280 and also bought a Philips SPC 900NC webcam with mic. (cam seems to works fne) to try out the new Skype for linux with video support, but when I try to make a test call I get the following error:
```
Call Failed: Problem with Audio Playback.
```

When I go to Skype's  Options -> Sound Devices I can choose the following devices and starts with 'Default Device (default)'

Intel ICH6 (hw:ICH6,4)
Intel ICH6 (plughw:ICH6,4)
USB Device 0x471:0x329 (hw:U0x4710x329,0)
USB Device 0x471:x329 (plughw:UOX4710x329,0)
Intel ICH6 (hw:ICH6,0)
Intel ICH6 (plughw:ICH6,0)
Intel ICH6 (hw:ICH6,1)
Intel ICH6 (plughw:ICH6,1)
Intel ICH6 (hw:ICH6,2)
Intel ICH6 (plughw:ICH6,2)
Intel ICH6 (hw:ICH6,3)
Intel ICH6 (plughw:ICH6,3)

I allready tried every option without luck. My system is Ubuntu 7.10 (gutsy) and my sound works great with programs like VLC or system sounds etc.

lspci gives me: ```
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03
```
Alsamixer looks OK and shows 3 devices
0:Intel ICH6 (alsa mixer)
1:USB Device 0x471:0x329 (alsa mixer)
2:Analog Devices AD1981B (OSS mixer)

Any idea how I can get my audio to work with the 2.0 beta?

---

### Post by ivago on 2007-12-03
could it be this card only works with the old OSS system? cuz when I try to test and select ALSA i get
```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Kan bron niet openen om te schrijven.
```
something in dutch saying it can't open the source to write to ...

any ideas?

---

### Post by ivago on 2007-12-06
got it working, turned out there was an old .asoundrc file in my $HOME dir wich messed up my audio config... audio and video are working like a charm now :)

---

