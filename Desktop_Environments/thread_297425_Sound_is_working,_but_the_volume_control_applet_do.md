---
title: "Sound is working, but the volume control applet does not"
date: 2006-11-11
forum: Desktop Environments
---

### Post by dpm on 2006-11-11
Hi, 

I've got a little annoyance that I've been experiencing since Breezy. It is not a real problem, since I've got a functional system, but I thought now that I'm using Edgy and everything is working nearly as expected, I'd try to solve this as well.

The issue is the following:

Sound is working perfectly fine. I can use rhythmbox, banshee, beep media player or any other music player and listen to music and change the volume setting from within each one of those apps.

However, I would like to be able to change the volume level from a central location that is always accessible. Therefore, I'm trying to add the volume control applet to my gnome panel. But when I do this, changing the volume level from the applet has no effect whatsoever. I've tried different combinations of device and tracks under the applet's preferences, but still no luck.

Under System>Multimedia Systems Selector I've got ALSA selected as the default output plugin. Under the 'device' dropdown menu of the 'volume control preferences' of the applet I select "VIA 8237 (Alsa mixer)", which I believe is my (on-board) soundcard, although I've also got another "C-Media Electronics CMI9761 (OSS Mixer)" device entry. In any case, I've tried both devices and the "Master" track, but it does no difference. Whatever I do, changing the volume through the volume control applet still does not work.

So any comments on how to solve this or on how the volume control plays together with alsa/oss will be greatly appreciated.

Thanks.

---

### Post by jazzgossen on 2006-11-11
I have ALSA and an nForce onboard sound card. I have the volume applet set to control the "surround" audio channel, and that works as I would expect the master volume setting to work. Strange, though.

---

### Post by dpm on 2006-11-12
Bummer. It seems to be a more or less known bug that has been around for some time now.

A workaround is to choose the PCM track instead of Master under the "Volume Control Preferences".

---

