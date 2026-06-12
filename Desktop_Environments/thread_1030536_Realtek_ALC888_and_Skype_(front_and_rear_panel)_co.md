---
title: "Realtek ALC888 and Skype (front and rear panel) configuration - Ubuntu 8.10 Intrepid"
date: 2009-01-04
forum: Desktop Environments
---

### Post by slayer^_^ on 2009-01-04
Skype is the most diffused VOIP application worldwide, in Ubuntu 8.10 it needs to be configured. In this thread I'll show how to configure it with the audio device RealtekALC888.

**Step 1) BIOS**
Be sure to ENABLE the HD audio and the front panel (they're set by default on auto): set them to ENABLE.

**Step 2) Skype**
In the Options / Audio Devices section, be sure it is set like this: 

HDA VIA VT82xx (hw:VT82xx,0)
pulse
pulse

The device of the first section may change (for example (hw:Intel,0) ).

Apply and exit

**Step 3) System --> Preferences --> Audio**
Be sure it's set liek this:

Automatic Identification
Automatic Identification
Automatic Identification
ALSA - Advanced Linux Sound Architecture
HDA VIA VT82xx (ALSA mixer)

again, the last voice may change... be sure it is the most possible similar to the one I've specified.

**Step 4) Volume Regulation**
Double-click on the audio icon on the top-right of your desktop;
Click on "Preferences" ; Enable everything you can.

In the "Switches" section, just enable everything

in the "Options" section, select "Mic" twice (if you're using the rear panel for the microphone, or "Front Mic" twice (if you're using the front panel).


It works for me, it should work for you. Let me know if something doesn't work for you, we'll manage to get it to work ;)

Cheers :P

---

### Post by keithld on 2009-01-04
I pretty much have the same onboard sound card and this is what I did in a Terminal to get SKYPE working... (From one of the tutorials here)...

killall pulseaudio
sudo aptitude remove pulseaudio
sudo aptitude install esound
sudo aptitude remove /etc/X11/Xsession.d/70pulseaudio

It works great...  :D

---

### Post by slayer^_^ on 2009-01-05
i believe it's just a matter of configuration... why killing services and removing libraries? I don't understand :D

The biggest part of the problem is activating the front panel in the bios though...

---

### Post by keithld on 2009-01-05
For me at the time after searching around for quite some time, it was the quickest solution to get SKYPE working...

[SKYPE](https://help.ubuntu.com/community/Skype) <---From the Ubuntu Tutorials...

---

### Post by slayer^_^ on 2009-01-05
you should see that it is not a solution, but a workaround... why removing pulseaudio, that is one of the brand-new implementations of Intrepid Ibex, when it is just a matter of properly configuring your hardware? (i.e. telling skype to use pulseaudio and your pc to use the front mic as input source).

With my configuration tips i didn't add or remove a single package and it works... most important, i hadn't to use any terminal commands at all. 

I don't want to claim that my solution is better, of course, but **with this sound card** it is the most simple. I always preferred the simplest things :)

Best regards

---

### Post by keithld on 2009-01-05
Yours is a good solution, had I seen it before I did what I did I would have done it your way...:D

---

### Post by slayer^_^ on 2009-01-06
next time :)

thanx for your answer !!

---

