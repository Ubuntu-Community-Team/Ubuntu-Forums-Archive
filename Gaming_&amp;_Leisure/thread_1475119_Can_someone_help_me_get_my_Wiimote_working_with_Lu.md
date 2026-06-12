---
title: "Can someone help me get my Wiimote working with Lucid and Gfceu?"
date: 2010-05-06
forum: Gaming &amp; Leisure
---

### Post by cdwillis on 2010-05-06
I've installed the packages listed here: [https://help.ubuntu.com/comhttps://help.ubuntu.com/community/CWiiDmunity/CWiiD](https://help.ubuntu.com/comhttps://help.ubuntu.com/community/CWiiDmunity/CWiiD)

I started wmgui and it shows the inputs for the buttons lighting up, but gfceu won't recognize any input when I press the buttons. I changed the /etc/cwiid/wminput/buttons file to this:

```
#buttons

Wiimote.A		= BTN_LEFT
Wiimote.B		= BTN_RIGHT
Wiimote.Up		= KEY_UP
Wiimote.Down	= KEY_DOWN
Wiimote.Left	= KEY_LEFT
Wiimote.Right	= KEY_RIGHT

Wiimote.Minus	= KEY_A
Wiimote.Plus	= KEY_S
Wiimote.Home	= KEY_Q
Wiimote.1		= KEY_Z
Wiimote.2		= KEY_X

Nunchuk.C		= BTN_LEFT
Nunchuk.Z		= BTN_RIGHT

Classic.Up		= KEY_UP
Classic.Down	= KEY_DOWN
Classic.Left	= KEY_LEFT
Classic.Right	= KEY_RIGHT
Classic.Minus	= KEY_BACK
Classic.Plus	= KEY_FORWARD
Classic.Home	= KEY_HOME
Classic.A		= BTN_LEFT
Classic.B		= BTN_RIGHT
#Classic.X		= 
#Classic.Y		= 
#Classic.ZL		= 
#Classic.ZR		= 
#Classic.L		= 
#Classic.R		= 
```

I just don't understand why it doesn't work. Any help would be GREATLY appreciated.

---

