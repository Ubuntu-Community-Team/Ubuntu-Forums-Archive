---
title: "[SOLVED] 06a3:ff0c Saitek PLC Cyborg Force Rumble Pad P2500"
date: 2008-07-02
forum: Gaming &amp; Leisure
---

### Post by starcannon on 2008-07-02
Here's a little guide for getting this gamepad working in kxmame:

```
sudo apt-get install xserver-xorg-input-joystick
```

Now either plug your joystick in, or unplug it and then plug it back in.

Open kxmame:
[INDENT]Then:[/INDENT]
[INDENT][INDENT]Settings-->Configure Kxmame-->Controllers[/INDENT][/INDENT]
[INDENT][INDENT][INDENT][LIST]
[*]Joystick type: Standard joystick
[*]Joystick device prefix: /dev/input/js0
[/LIST][/INDENT][/INDENT][/INDENT]

Your 06a3:ff0c Saitek PLC Cyborg Force Rumble Pad P2500 should now be working in Mame (will even let you navigate the Mame window.

Fire up a game and press the TAB key, you can set global or per game settings.

Enjoy,
~starcannon

---

