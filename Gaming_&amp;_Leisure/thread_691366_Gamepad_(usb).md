---
title: "Gamepad (usb)"
date: 2008-02-08
forum: Gaming &amp; Leisure
---

### Post by joeri_83 on 2008-02-08
Hi,

I am trying to get a generic usb controller (it's an unbranded GameStop controller) to work in Ubuntu. When I type in cat /dev/input/js0 and press buttons things are printed in the terminal, so I assume Ubuntu knows it's there, but I cannot use it in any games (GXMame specifically, but not in Mania Drive either). I have installed joystick and jscalibrator and chmod js0 to 666.

What can I try next?

---

### Post by acoustibop on 2008-02-08
jscalibrator is probably your problem, joeri_83.  Uninstall it, including the configuration.

It has a tendency to disable controller buttons/axes while still reporting them as working.

---

### Post by joeri_83 on 2008-02-08
I tried it, and assuming that the config is ~/.joystick it still does not work. (The right analog stick left seems to now do the same as button 0, while right stick up is button 1, but neither the left stick or d-pad works). It's one of those controllers with a mode button for d-pad/analog, but it does not seem to matter whether it's on or not.

Thanks for trying to help me! Any further ideas? Have I missed some config files?

---

### Post by joeri_83 on 2008-02-08
Rather weirdly, all of a sudden Wahcade throws this at me when I try to start it:

> Traceback (most recent call last):
  File "wahcade.py", line 72, in <module>
    app = WinMain(options)
  File "/home/balki/projects/wahcade/debian/wahcade/usr/share/games/wahcade/win_main.py", line 275, in __init__
    self.load_emulator()
  File "/home/balki/projects/wahcade/debian/wahcade/usr/share/games/wahcade/win_main.py", line 897, in load_emulator
    self.lblEmulatorName.set_text(self.emu_ini.get('emulator_title'))
  File "/home/balki/projects/wahcade/debian/wahcade/usr/share/games/wahcade/mamewah_ini.py", line 111, in get
    if self.ini_dict.has_key(option):
AttributeError: MameWahIni instance has no attribute 'ini_dict'


And it never really starts, even though it worked just fine just a little while ago. I've tried re-installing and completely removing it and installing it again; still same problem. What gives?

---

### Post by joeri_83 on 2008-02-09
Any ideas? This really bugs me, since it was all working so well.

---

