---
title: "Star Wars-knights of the old republic 2 sith lords"
date: 2007-10-30
forum: Gaming &amp; Leisure
---

### Post by Eddie002Fast on 2007-10-30
ok i got SWkotor2 installed and all the Wine settings configured......but i cant get the game too load the swkotor2 config from game window (scan hardware) came up with 1 item that failed.....

Video Failed  
error -- [] 16MB
graphics required: 32MB OpenGL 1.4 compatible PCI or AGP 3D hardware accelerator with hardware transform and lighting (T&L) capability required

!?!?!?!?!?!?!?!?!?!?!?!?!?!?!?!??!?!?!?!?! How i fix that ? :(

---

### Post by cogadh on 2007-10-31
You don't, the hardware scan will always fail because it is looking for Windows drivers that are not present in Wine. As long as you already have the accelerated drivers for your video card installed, you can eliminate some of the error by setting Wine registry entries for you card's true video memory. It might also be helpful to change the DirectDraw renderer to OpenGL instead of the default GDI. See the Wine "Useful Registry Keys" page for details:
[http://wiki.winehq.org/UsefulRegistryKeys](http://wiki.winehq.org/UsefulRegistryKeys)

The game should still run despite the errors, just make sure you turn off hardware mouse in the game options, otherwise the cursor will be invisible.

---

### Post by Eddie002Fast on 2007-10-31
I had got past the lucas arts and obsidian preview then the game crashed.........also in the SWkotor2 config........has an option for V-Sync should i check that option? Also now i cant get the game too launch at all and i followed the wine config settings list exactly...........i set the DirectDrawRenderer and the VideoMemorySize keys i had too make them but they are there now and i still can get it too work ? and i  manually set my vram too correct amount,,,,,,,,,,,,,,,,,,,,,any ideas on what it might be the reason why i still cant get too the game play part LOL!

---

### Post by cogadh on 2007-10-31
The copy protection on the game prevents it from running in Wine without a cracked executable. Don't ask me where or how to get one, it is a touchy subject around here (rightly so).

---

