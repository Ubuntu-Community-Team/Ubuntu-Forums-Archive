---
title: "Wiimote Classic Controller Joystick?"
date: 2008-06-15
forum: Gaming &amp; Leisure
---

### Post by Nikayah on 2008-06-15
I've been looking at using my wiimote (classic controller in particular) with an emulator (mupen64plus) I've looked at multiple programs including CWiid, libwiimote, and xwii. Xwii is the only one that I've seen that is compatible with mupen although it does not register the joysticks as joysticks but instead button presses. I am looking for a program (or a tut) that registers both joysticks in the classic controller (and possibly the nunchuck) as actual joysticks.Cwiid looked like it could do this, but I was unsure as to how.

EDIT: It looks like Cwiid's wminput does this, but i can't get it to work, can anyone give me a hand?

---

### Post by MrSootentai on 2008-07-09
I have the same question, I noe you can edit and create your own profiles with the XWii but because I used the deb (and the source code make doesnt work) I can't figure out how to load a custom profile.

---

### Post by signifer123 on 2008-07-10
> **MrSootentai said:**
> I have the same question, I noe you can edit and create your own profiles with the XWii but because I used the deb (and the source code make doesnt work) I can't figure out how to load a custom profile.

I use XWii from source, and it worked fine, the command is xwii then profile:

Example for me:

~/src/xwii# ./xwii profiles/mikeBase.xwii

theres the folder "profiles" which I have mikeBase.xwii in.

---

### Post by dakilla on 2009-10-11
my nunchucks needs to be calibrated, any one knows where i can do this?
they think its "left" when joystick is in "center".
happens on booth my wiimotes/nunchucks. using Xwii 2.8.

---

### Post by ateijelo on 2009-11-08
wminput might be the answer. It served me well to use a wiimote+nunchuk with mupen64plus. I had to create a new config file based on /etc/cwiid/wminput/gamepad and I had to reconfigure the input in mupen, but it didn't require much effort anyway.

---

### Post by vintermann on 2010-03-29
I have tried to do what ateijelo did, but I find no way to configure the nunchuck stick as a mouse. Setting 

```

Nunchuk.Stick.X = ABS_X
Nunchuk.Stick.Y = ABS_Y
```

just causes wminput to segfault.

I have a classic controller also, but using the default config file for gamepads (which should work) results in something Mupen doesn't detect. I see that sometimes there appear devices under /dev/input/jsX and /dev/input/eventX, and these devices appear to be written to when I press buttons, but Mupen still doesn't find them. Sometimes the devices don't appear at all.

---

### Post by Tyr42 on 2010-12-29
If you don't mind using a nunchuck, [wm2js]("http://ubuntuforums.org/showthread.php?t=1386430&page=2") (after being modified somewhat by the smart people of this forum) works very well for me.  
I am actually just trying to extend it to work with the classic controller, since I just bought one, but it might take a backseat to homework.  I hope to at least factor out the hard coding of the wiimote's bluetooth address in the source file to a command line option.  I hope to get that done today.

---

