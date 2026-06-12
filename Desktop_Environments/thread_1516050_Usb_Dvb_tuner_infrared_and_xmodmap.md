---
title: "Usb Dvb tuner infrared and xmodmap"
date: 2010-06-23
forum: Desktop Environments
---

### Post by michaelAust on 2010-06-23
I have a TinyUsb Dvb tuner which gets recognized as a Twinhan vp7045 (which I believe it is) and it works very well. It also contains an infrared receiver for the remote control which I believe acts as a usb hid keyboard. This means that when I press a button on the remote it sends a keypress to the computer. I have set up a file ~.Xmodmap, which contains definitions to remap two of the remote buttons to useful keypresses in kaffeine (mute and play/pause).
Code
keycode 127 = space
keycode 231 = u

This has been working perfectly in Kubuntu Hardy for the last couple of years. I recently switched to Ubuntu Lucid, and it works fine if I boot the computer with the usb tuner plugged in, but if I unplug it and plug it in again the pause and mute buttons stop working (the right and left arrow buttons on the remote (which are not in ~.Xmodmap) still work. 'xmodmap -pke' still shows the correct definitions as above. Xev does register a keypress for both the pause and mute buttons before and after unplugging and replugging, before it shows space and u, but after it doesn't. (Unplugging was no problem in Hardy.)

So it seems that unplugging and repluggiing it just stops xmodmap from working properly, the device is still sending the hid keys.

Any ideas ?

---

### Post by michaelAust on 2010-06-24
Found the answer.

Run
```
xmodmap ~/.Xmodmap

```
after the usb tuner is unplugged and replugged restores the right settings.

---

