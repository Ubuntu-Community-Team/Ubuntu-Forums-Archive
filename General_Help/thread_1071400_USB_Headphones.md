---
title: "USB Headphones"
date: 2009-02-16
forum: General Help
---

### Post by homerj14 on 2009-02-16
Hello, I cannot get my usb headphones to work in ubuntu 8.10, my speakers work just fine. please let me know if this can be solved :D thanks in advance.

---

### Post by kostkon on 2009-02-16
Install the *PulseAudio Device Chooser* utility (it will have a menu entry in *Applications &#8594; Sound & Video*). Run it, left-click on its icon in your system tray and select *Volume Control*.

From there you will be able to send the audio stream of one application from yours speakers in real time. In the *Playback* tab you should see the audio streams of your running applications (the ones that produce audio only, of course). Right-click on one and select *Move Stream...* to move its audio to the device you want.

In the *Input Devices* and *Output Devices* tabs you can set the default input and output device to be used by your applications. Right-click on the device you want and enable the *Default* option.

For example, you can set your USB headset as the default output device and all your applications will send their audio there by default.


For this to work, you should set your sound playbacks in *System &#8594; Preferences &#8594; Sound* to *Autodetect* (and if you want your inputs to *PulseAudio*), in case you have changed them.

Hope that helps...

---

