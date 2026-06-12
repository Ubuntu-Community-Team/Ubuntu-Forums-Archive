---
title: "usb foot pedal not recognized"
date: 2007-10-21
forum: Gaming &amp; Leisure
---

### Post by daka on 2007-10-21
This is for transcription purposes

The windows software has been installed using wine but the software (ExpressScribe) does not find the foot pedal.  When I do lsusb I get the folowing, indicating that it is recognized as a USB device.

...  Bus 002 Device 008: ID 05f3:00ff PI Engineering, Inc. 

Any suggestions?  Other people seem to be able to get this working easily in Linux, according to the product forum.

looks like it is recognized as usb device but needs something more to be recognized by the software... some configuring... probably something simple, but I am new to this.

Daka

---

### Post by Qwerty_ on 2007-10-21
Does wine work with usb?

---

### Post by daka on 2007-10-21
In the forum for these pedals many people claim success in running the software in Linux under Wine so I suspect Wine does work with USB

---

### Post by daka on 2007-10-22
Solved by installing Gutsy... now all is well!!!!!!:guitar:

---

### Post by zh137dz on 2008-04-01
I have Gutsy 7.10 installed, with Express Scribe running under Wine and it still won't recognize my pedal. I have a VEC Infinity USB pedal. I ran the lsusb command and it sure enough is showing up so I'm assuming NCH isn't talking correctly to it or something. Any help?

---

### Post by jasongray on 2008-06-16
I would also like some help with this; please if anyone has any suggestions at all it would be appreciated.  I have two playback devices that work in Windows with Express Scribe: a Genius gameport steering wheel foot pedal and a USB Logitech gamepad. I am using Hardy.  

Both of these devices show up fine when I run an lsusb and lsmod check; I can give you the output on those.  But Express Scribe doesn't recognize them at all.  This is the only thing preventing me from switching over to Ubuntu at the moment because I need to do my work on a piece of transcription software.

---

### Post by schardein on 2008-09-02
Just adding another request for help.  I've got StartStop installed in Wine and it will play back audio files, but it doesn't seem to recognize the USB foot pedal.  For transcriptionists, this foot pedal is crucial for controlling audio playback so that the audio doesn't progress faster than they can type.

If anyone can help with a solution for making these apps recognize the USB foot pedals from Wine, it will prevent a Windows dual-boot or virtual machine installation.

---

### Post by katiekat on 2012-02-15
Hi, I am also having trouble getting Express Scribe (v 5.48) to recognize my Infinity USB 2 foot pedal (in Ubuntu 10.04). Has anyone been able to solve this problem?

Thanks!
Katie

---

### Post by katiekat on 2012-02-15
I mean Express Scribe v 5.48

---

### Post by zerubbabel on 2012-09-27
Has anyone found any foot pedal that works under Linux?

(Preferably, one that works with the Windows version of Express Scribe running under Wine?)

---

