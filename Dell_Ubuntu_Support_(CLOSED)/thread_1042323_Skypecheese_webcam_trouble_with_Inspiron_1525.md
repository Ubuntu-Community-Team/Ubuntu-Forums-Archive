---
title: "Skype/cheese webcam trouble with Inspiron 1525"
date: 2009-01-17
forum: Dell Ubuntu Support (CLOSED)
---

### Post by JoeJoeMa on 2009-01-17
I have installed ubuntu 8.10

and for the life of me i can't get cheese or skype to work

Everything is great except, the graphics driver is a little wonky i think, but i could  be wrong.

But the real problem is that my integrated webcam is near useless, besides the blue light coming on, it just sorta sits there are looks semi-cool

I've looked over the  countless other threads about this problem but for some reason i haven't been able to fix/follow the problem/solution

any help would be great on the subject

---

### Post by Bylund951 on 2009-01-17
Im having the same problem with my Toshiba satellite laptop w/integrated webcam.

---

### Post by llamakc on 2009-01-17
> **JoeJoeMa said:**
> I have installed ubuntu 8.10

and for the life of me i can't get cheese or skype to work

Everything is great except, the graphics driver is a little wonky i think, but i could  be wrong.

But the real problem is that my integrated webcam is near useless, besides the blue light coming on, it just sorta sits there are looks semi-cool

I've looked over the  countless other threads about this problem but for some reason i haven't been able to fix/follow the problem/solution

any help would be great on the subject

Skype & aMSN work fine for me on my 1525. Cheese locks up and I have to force-quit.

In (the menu) SYSTEM > PREFERENCES > SOUND I have Autodetect on the 1st three and ALSA on 'Sound Capture'.

Next, run `gstreamer-properties` from the Terminal (or ALT-F2). I have "Default" set for the default output plugin, and ALSA [and Default for the device] for Default Input.

On the video tab of gstreamer-properties I have Plugin: Autodetect, and Video for Linux 2 for the default input plugin with "Laptop Integrated Webcam" for the Device.

---

### Post by JoeJoeMa on 2009-01-18
> **llamakc said:**
> Skype & aMSN work fine for me on my 1525. Cheese locks up and I have to force-quit.

In (the menu) SYSTEM > PREFERENCES > SOUND I have Autodetect on the 1st three and ALSA on 'Sound Capture'.

Next, run `gstreamer-properties` from the Terminal (or ALT-F2). I have "Default" set for the default output plugin, and ALSA [and Default for the device] for Default Input.

On the video tab of gstreamer-properties I have Plugin: Autodetect, and Video for Linux 2 for the default input plugin with "Laptop Integrated Webcam" for the Device.


For gstreamer-properties sound I don't have the option for default as the output plugin, i have autodetect, ALSA, OSS, Pulseaudio, and custom
and then the device says unsupported, for default input everything looks fine... 

the Video the output has autodetect two X window system, and a custom, then the device says unsupported, the default input looks fine though, but when i click test it says "video for linux 2 (v4l2): Device '/dev/
video0' cannot capture at 1280x1024

---

### Post by llamakc on 2009-01-18
What are your settings in Skype?

---

### Post by JoeJoeMa on 2009-01-19
I'm assuming you mean the sound and video devices in options

Sound In is set as default
Sound Out is set as default
Ringing is set as default

the test sound doesn't seem to work, and when i make a test call An error comes up saying "Problem with audio playback"

The video however seems to work just fine... Which makes me wonder why cheese doesn't work...

---

### Post by llamakc on 2009-01-19
In Skype I had to set the following in Sound Devices:

Sound In: HDA Intel (hw:Intel,0)

Sound out: HDA Intel (hw:Intel,0)

Ringing: HDA Intel (hw:Intel,0)

And I have unchecked "Allow Skype to automatically adjust my mixer levels"

---

### Post by JoeJoeMa on 2009-01-19
The webcam sometime wiggs out, but over all its working. Sweet thanks! One problem down!

---

### Post by Avenger1432 on 2009-03-16
I am having a problem with my audio playback...just like what the problem was in this thread.. and my video works just fine.

Just no sound recording...  I have the same settings as mentioned before.

Someone please  help?

---

### Post by Shinobi3213 on 2009-03-23
> **JoeJoeMa said:**
> For gstreamer-properties sound I don't have the option for default as the output plugin, i have autodetect, ALSA, OSS, Pulseaudio, and custom
and then the device says unsupported, for default input everything looks fine... 

the Video the output has autodetect two X window system, and a custom, then the device says unsupported, the default input looks fine though, but when i click test it says "video for linux 2 (v4l2): Device '/dev/
video0' cannot capture at 1280x1024

Thanks for the advice. I just got my 1525 back from the shop and installed 8.10 and I couldn't get the camera to work to save my life.

---

