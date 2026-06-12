---
title: "Latitude e6500 microphone"
date: 2008-11-07
forum: Dell Ubuntu Support (CLOSED)
---

### Post by thattallguy on 2008-11-07
Working with a new Latitude E6500 and Ubuntu 8.10.  Just about everything works - but I tried to install Skype and discovered that the mic doesn't record sound!  Same is true of Ekiga and the Sound Recorder app, so it's not Skype.

It appears to be detected properly -- in Sound Recorder, for example, the capture process works, and the level meter appears and fluctuates slightly -- but it does not respond to even very loud sounds, nor can you hear anything but a hiss when playing back.

The mic works in Vista.  Also, plugging a microphone into the jack works -- that sound is captured.  It's a problem with the built-in mic.

Any clues?

---

### Post by shingalated on 2008-11-07
Make sure the correct microphone input is selected.  If you double click the volume icon, you should be able to select which one.  I think for the M1330 it is "Digital Mic"  Try that one if you have it as an option.

---

### Post by thattallguy on 2008-11-07
In Sound Recorder, there is only one option for "Record from input:" called "capture".  In Skype, I have tried all the available options, including "HDA Intel" (2 types), "pulse", and "hdmi".  No change.

---

### Post by shingalated on 2008-11-07
the option I'm talking about isn't in sound recorder, it is in the volume control.  If you double click the volume control applet icon, probably located in the top panel, and go to the options tab, there should some options for which microphone input to use.

---

### Post by thattallguy on 2008-11-08
Hm, that may have been part of the problem (mic levels were 0) but I still can't get it to work.

Volume Control shows two Capture options:
"ALSA PCM on front:0 (STAC92xx Analog) via DMA (PulseAudio Mixer)" and 
"Monitor Source of ALSA PCM on front:0 (STAC92xx Analog) via DMA (PulseAudio Mixer)"
There is also a Recording tab on the "HDA Intel (Alsa mixer)" selection.

All of these levels are now at max.

I see that when I switch between devices, the microphone appears with a little "x" icon over it that disappears immediately, so I'm guessing I'm switching between inputs -- I've tried recording using SR while each of these is activated.  No success anywhere.  I have even tried closing the application (in case that's necessary to save the setting) on each setting before reopening Sound Recorder -- nothing.

I'm guessing that the correct device is HDA Intel for two reasons: first, that's what I see in Skype on Vista, and second, the "Playback: ALSA PCM (etc etc)" also shows a little red "x" icon, suggesting that the HDA Intel is providing the output, which is working.

What am I missing?

---

### Post by xvolter on 2008-12-04
I myself just bought a Dell Latitude E6500. I didn't get it with Vista however.. I forced Dell into shipping it without Vista else I wouldn't buy it.

However, when I installed Ubuntu my Mic also didn't want to work. I tried a few things out and finally got it to work. It was saddening when it happened however, because it was very simple.

You already stated that the Mic is detected, but the mic is always disab led. This is how mine was, and whenever I attempted to enable the mic it would disable itself after closing.

So here's how you can fix it..

Double click on the sound icon and open your volume control. Select the device HDA Intel (Alsa) [High Definition Audio Device]. Click "Preferences" and have the following items selected:
 * Digital Mic 1
 * Digital Input Source

After clicking close, goto the Options tab. Select "Digital Mic 1" for your Digital Input Source. In the Recording tab make sure your Digital Mic 1 is turned up, all the way for testing.


Then make sure your sound settings are using ALSA, System > Preferences > Sound. I have everything selected to "ALSA - Advanced Linux Sound Architecture".


Now test her out. Open "Sound Recorder" and hit the record button. Say the following sentence twice: "Linux is great. Linux is greater than Windows. If the box says Windows 95 or greater, then Linux is the greater. Macs are PCs." Hit "Stop" and then hit "Play". I recommend making sure your playback volume is up as well that way you can hear your voice. At first my volume was muted when I hit play but I realized it was when I noticed I couldn't hear Pandora playing.

If you hear yourself, you've configured your Dell Latitude E6500 with Ubuntu correctly. If you don't hear yourself something is wrong with your audio settings.

Hopefully that helps.


EDIT::
After this I had a few issues configuring Skype properly. Actually, my audioplayback stopped working. In the Audio Devices settings for Skype if I use the following it worked again:
Sound In: HDA Intel (hw:Intel,0)
Sound Out: pulse
Ringing: pulse

Then apply and close. Open your volume control again and click "Preferences" (assuming your default is "HDA Intel (Alsa mixer)" - if it's not, select that and also change your default device in System > Preferences > Sound). In the "Preferences" window make sure you have the following items selected:
* Capture
* Capture 1

Now in the Recording tab make sure both "Capture" and "Capture 1" are turned all the way down and have the red X over the mic. Then turn "Digital Mic 1" all the way up and make sure there is no red X on that mic. Close Volume Control. Then make a Skype test call to confirm.

---

### Post by thattallguy on 2008-12-04
xvolter:

Spook-tacular!  Fixed the problem perfectly.  (I have "HDA Intel (Alsa mixer)" instead of "High Definition Audio Device" but it does the job.)

Many thanks!

--ttg

---

### Post by jbaloul on 2008-12-05
hey guys,
I am thinking of getting this model too...
who better to ask than one that already took the plunge...

Are you overall happy with the performance?
Do all the buttons work as well?
How bout the integrated cam?
Can you give me a good review of it now that you have been using it for a while?

thanks very much,
Jacob

---

### Post by thattallguy on 2008-12-05
jbaloul,

I'd call it 4 out of 5 so far.

Pretty much all the hardware works now.  I haven't tested all of the outputs under Linux yet, but suspend mostly works (95% of the time on Linux,) and everything else works after some fiddling (not yet tested: <strike>eSATA</strike>, HDMI & Bluetooth.)  (EDIT: eSATA works.)

If I had it to do over again I would get the NVIDIA graphics card, not the Intel, though -- the performance of the graphics card is dragging the rest of the machine down.  Also, the Intel graphics drivers haven't caught up to the hardware yet -- Fedora is running with an unstable driver that crashes a lot, and Ubuntu is running stable with old drivers that hasically run unaccelerated.  New drivers for Intel are not anticipated to be released on Ubuntu until at least 9.04.

Otherwise I've been satisfied with the machine.

---

### Post by jbaloul on 2008-12-07
Thank you very much!
Well put.
I will take everything you said into consideration.

Enjoy your new laptop,
Jacob

---

### Post by b4rt on 2008-12-08
xvolter:

After applying your tips, the internal mic works great, but now the internal webcam doesn't work anymore... (nor cheese nor skype)

I think they are somehow connected...

Greetz,

B

---

### Post by windfix on 2009-01-24
I am using the E6500 too, just noting that the card reader picked up my SD card flawlessly and assigned it a nice SD-card icon immediately.  Happy so far.

I got the NVidia graphics, and it is powering twin 20" panels flawlessly.  However, the standard "Screen Resolution" applet does not work at all.  I have to use the NVidia X Server applet to reconfigure displays every time I dock or undock - a bit of a hassle, but it does work.


> **jbaloul said:**
> hey guys,
I am thinking of getting this model too...
who better to ask than one that already took the plunge...

Are you overall happy with the performance?
Do all the buttons work as well?
How bout the integrated cam?
Can you give me a good review of it now that you have been using it for a while?

thanks very much,
Jacob

---

