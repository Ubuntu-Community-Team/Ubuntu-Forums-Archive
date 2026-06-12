---
title: "Saitek P990 Gamepad *almost* works in Mupen64 v0.5 with Blight plugin in Gutsy"
date: 2008-03-23
forum: Gaming &amp; Leisure
---

### Post by Giggity on 2008-03-23
I just bought a Saitek P990 for my Gutsy box hoping to play Mario64 using the Mupen64 emulator version 0.5.  The graphics and sound work great in this emulator, but there is a problem using the gamepad.

I can use the blight plugin 0.0.10 config and select a button for every action, but there's one pretty important problem that I need to find a solution for:

*** Up and Down work on the D-Pad and Analog stick, but Left and Right do not!

All the other buttons map well, and if anyone can help me fill in this blank, I'd appreciate it since that would make N64 emulation achieve platinum status on my Ubuntu box.

Attached is the blight_input.conf that I've set up for use.  If there's anything else you need, please let me know!   Thanks!

Note:  I have edited this to reflect the fact that I found out why the Analog Stick wasn't working for me (it was because I had set the "Analog On/Off" button to work as the Start button), however Left and Right still don't work with either the D-Pad or Analog...

---

### Post by Giggity on 2008-03-23
*** SOLVED ***

Never mind... I'm just dumb!

Here's what happened:  I had the analog support enabled when I set the D-Pad buttons for Left and Right, which put them on the "V-Axis" instead of the X-Axis (which is what one wants when playing Mario64).  I had no idea what that meant so I thought it wasn't a problem.

Then, since I had the "Analog On/Off" button set to be the Start button, every time I pushed that, it turned on/off the analog stick.  So when I set the stick, it was set to the W and V axes instead of the X and Y axes... that's not what you want to play Mario.

So, crisis averted... thanks for giving me a place to think out loud!

---

