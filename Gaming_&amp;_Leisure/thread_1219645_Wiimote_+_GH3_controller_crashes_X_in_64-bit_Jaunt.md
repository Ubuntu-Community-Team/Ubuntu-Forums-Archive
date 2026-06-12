---
title: "Wiimote + GH3 controller crashes X in 64-bit Jaunty"
date: 2009-07-22
forum: Gaming &amp; Leisure
---

### Post by marshmallow1304 on 2009-07-22
I'm trying to use a Wii GH3 guitar, a GHWT guitar, and GHWT drums with FoFiX 64-bit.

This is my /etc/cwiid/wminupt/gh3 file:
```
# Wii Guitar profile for Frets on Fire
Classic.Down=KEY_ENTER #Strum
Classic.Up=KEY_ENTER
Classic.Dpad.X = ABS_X
Classic.Dpad.Y = ABS_Y
Classic.LStick.X = ABS_HAT0X
Classic.LStick.Y = ABS_HAT0Y
Classic.RStick.X = ABS_HAT1X
Classic.RStick.Y = ABS_HAT1Y
Classic.A = KEY_F1 #First Fret starting at top of wiiguitar
Classic.B = KEY_F2 #Second Fret
Classic.X = KEY_F3 #Third Fret
Classic.Y = KEY_F4 #Forth Fret
Classic.Minus = BTN_SELECT
Classic.Plus = KEY_ESC
Classic.Home = BTN_MODE
Classic.L = BTN_TL
Classic.R = BTN_TR
Classic.ZL = KEY_F5 #Fifth Fret
Classic.ZR = BTN_TR2
Wiimote.Left= KEY_LEFT
Wiimote.Up= KEY_LEFT
Wiimote.Down= KEY_DOWN
Wiimote.Right= KEY_DOWN
```
I then do ```
sudo wminput -c /etc/cwiid/wminput/gh3
```
At this point, when I use any of the fret buttons on the GH3 controller, X crashes and I end up back at the login screen.  When using the GHWT guitar, the fret buttons do nothing, but the buttons on the actual Wiimote cause the crash.
When I connect the Wiimote via wmgui, all buttons work and no crash occurs.

I have yet to try the GHWT drums.


Any ideas?

---

### Post by marshmallow1304 on 2009-07-23
bump

---

### Post by rednano12 on 2009-07-23
The guys at fretsonfire.net would probably be better at helping you with this. I'm  not sure if any of the local Linux users have GH guitars though... FoFiX is a great game.

---

### Post by marshmallow1304 on 2009-07-23
> **rednano12 said:**
> The guys at fretsonfire.net would probably be better at helping you with this.

I'll try asking there, but I thought that asking here would be more appropriate because this is not a problem with FoFiX.  AFAIK, it's a problem with the wiimote libraries.

---

### Post by manfrom3004 on 2009-07-28
I only use the wiimote and wminput, but I have the same problem with X crashinging. I dont have 64 bit ubuntu.

---

### Post by marshmallow1304 on 2009-07-28
I finally decided to work with it and I solved it by commenting out all of the config file, then uncommenting it line by line until I figured it out.

It turns out that
```
Classic.Dpad.X = ABS_X
Classic.Dpad.Y = ABS_Y
```
caused the crash.

The strange part though is that either one of those two lines by itself will not cause the crash, but when they're both used, the crash occurs.  So, to fix it, comment out or remove one of or both of those lines.

---

### Post by nazgul42 on 2009-08-01
Thank you, this helped me out.

---

### Post by ToeBee on 2009-08-13
Me too! And just to clarify, it is the ABS_X and ABS_Y that cause the problems, not the Dpad. I had the IR mapped to ABS_X and ABS_Y even though I'm not actually using it at the moment. I guess I'll comment them out and hope a fix comes down the pipe before I want to use it again :)

---

