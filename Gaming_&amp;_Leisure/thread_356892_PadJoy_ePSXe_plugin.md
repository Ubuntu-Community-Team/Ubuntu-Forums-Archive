---
title: "PadJoy ePSXe plugin"
date: 2007-02-08
forum: Gaming &amp; Leisure
---

### Post by Jarn on 2007-02-08
How does it work? I can't seem to figure it out. I open ePSXe, Config -> Ext. Game Pad, then I can't figure out how to set the controls. I click one of the buttons, Triangle for example, and hit a key on the keyboard. Nothing happens. Eventually, it stops looking for a keypress and the terminal says that no valid input was found.

---

### Post by po0f on 2007-02-09
Jarn,

The reason it's not reading any input is because padJoy is expecting events to come from a joystick device (/dev/js0 or /dev/input/js0), not your keyboard.  To set up your keyboard, navigate to Config->Game Pad->Pad 1.

---

### Post by Jarn on 2007-02-12
Then how do I do the special things PadJoy is capable of, like turbofire and macros?

---

### Post by Jarn on 2007-02-16
Bump.

---

### Post by po0f on 2007-02-16
Jarn,

Buy a joystick.  There are joystick-to-keyboard programs out there, but I'm not aware of a keyboard-to-joystick one.  You can pick up a decent gamepad for ~$20, and it feels way better than a keyboard for console games.  :)

---

