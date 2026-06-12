---
title: "wahcade + sdlmame help"
date: 2007-09-29
forum: Gaming &amp; Leisure
---

### Post by taehC on 2007-09-29
How do i update the game list?
i put more roms into the directory where wahcade looks for games, but when i go into wahcade it doesn't show them...
anyone help?

---

### Post by taehC on 2007-09-30
anyone?

---

### Post by taehC on 2007-09-30
can anyone help?

---

### Post by Bagleemo on 2007-12-14
You'd probably have more luck searching / posting here:

[http://www.anti-particle.com/forum/index.php](http://www.anti-particle.com/forum/index.php)

---

### Post by Meox on 2008-10-18
Actually it's very simple you go to wahcade press 2 game list -> generate game list and it'll show the new games

---

### Post by jukingeo on 2008-12-02
> **Meox said:**
> Actually it's very simple you go to wahcade press 2 game list -> generate game list and it'll show the new games

I managed to get WhaCade to work last night (with SDLMame), however, I have to use the keyboard to make selections and I want to use the joystick I have hooked up (PS2 controller via a USB adapter).  I have gone into the WahCade setup editor and did tick off joystick control, but that doesn't seem to work.

The joystick DOES work within a MAME game and I can play the game using the joystick...however, buttons for coining up, starting the game, do not work (probably just a mapping issue within SDLMame).  However, the joystick will not work at all in the WahCade interface and I do want to get that fixed as the whole point of the WahCade front end is to emulate a commercial arcade machine.   So I really don't want to see the Linux OS or use the keyboard in anyway (except for servicing).

Any help would be much appreciated.

Thanx,

Geo

---

### Post by williamts99 on 2009-10-24
> **taehC said:**
> How do i update the game list?
i put more roms into the directory where wahcade looks for games, but when i go into wahcade it doesn't show them...
anyone help?

Another way is to use Applications>Games>Wah!Cade Setup Editor
Click on the M.A.M.E Only tab
There is a blue refresh button after the XML/Data File text entry box that when you hover over it, it says 'Generate XML File'

If you activate that button, it will generate a new list for you.

Best Regards,
Williamts99

---

### Post by williamts99 on 2009-10-24
> **jukingeo said:**
> (PS2 controller via a USB adapter)

The joystick DOES work within a MAME game and I can play the game using the joystick...however, buttons for coining up, starting the game, do not work (probably just a mapping issue within SDLMame).  However, the joystick will not work at all in the WahCade interface

I just have to find a playstation 2 controller and I will test this for you with my adapter and see what I come up with.

Best Regards,
Williamts99

EDIT:
Ok, so I tested it with my PS DualShock controller, it was in analog mode the whole time with a FT8D1 PS/GC/XB/USB adapter.  In Wahcade I enabled the joystick checkbox, I mapped all controls that use the number 1 key to the controller start button, and 2 key to the controller select button.  Don't forget to save your settings before exiting the setup editor.

To map the controls in SDLmame, run it from a terminal, select Configure General Inputs, then Other Controls.  How you want to map it is completely up to you.  But it all worked out perfectly for me.

Enjoy

---

