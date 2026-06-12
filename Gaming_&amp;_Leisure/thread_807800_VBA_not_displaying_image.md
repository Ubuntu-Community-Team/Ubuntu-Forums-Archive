---
title: "VBA not displaying image"
date: 2008-05-26
forum: Gaming &amp; Leisure
---

### Post by Dynih on 2008-05-26
I've installed vbaexpress via synaptic, but the game window that appears when one loads a rom is blank; either grey or black in color. It claims at the top that it's running at "99%" or similar, but there's nothing to be seen and no sound.

How can I fix this?

---

### Post by Sockerdrickan on 2008-05-26
You can fix it by using my GB/C emulator. lol.

No GBA support though. [www.tuxemu.se.nu](www.tuxemu.se.nu)

---

### Post by disturbedite on 2008-05-26
@ Tux0r
do you ever plan on adding GBA support?

---

### Post by DoktorSeven on 2008-05-26
Some games running through VBA need specific things, like a BIOS image (don't ask where to find one, they're copyrighted and all that) or different sized/type backup memory, and it's sort of complex to get that going in VBA.

I've found Mednafen (should be in the repos as well) runs most GBA stuff just fine, though there's no GUI, you have to run it by commandline (**mednafen /path/to/roms/gamerom.zip** making sure to substitute the actual path and name of your game ROM in that command, such as **mednafen /media/cdrom/Mario.zip** as an example).

Also, check [here](http://mednafen.sourceforge.net/documentation/#features-gba) to specify backup memory type/size for some games, if they don't work or give you some error message about memory.  If it's not quite clear, navigate to .mednafen/sav/ in your home directory (note the dot, you have to show hidden files in your file browser) and create a file with the same name as the ROM filename, except use ".type" (no quotes) as the extension instead of .gba or .zip or whatever it has.  Open that file as a text file and put what it says, like **flash 128** or some other (just experiment).  I had to do this with a few ROMS to get them working.

---

### Post by Sockerdrickan on 2008-05-26
> **disturbedite said:**
> @ Tux0r
do you ever plan on adding GBA support?

No imo the games on the GBA are mostly SNES ports and zsnes owns at emulating the SNES.

---

### Post by Dynih on 2008-05-26
Ok, the flash 128 thing worked with mednafen. Is there any way to do the same thing with vba? I really don't like the key assignments with mednafen. If there's a way to change the key assignments in that, that would also be helpful

Thanks for the advice so far!

Also, Tux0r, while it's your prerogative to do as you wish, not all GBA games are SNES ports, e.g.: FF Tactics, PokeMon (admittedly arguably a GBC port), Advance Wars, etc.

---

### Post by acoustibop on 2008-05-26
In Mednafen, do Alt+Shift+1 to set key or controller assignments, Dynih.

---

### Post by DoktorSeven on 2008-05-26
I don't think the Linux version of VBA has that capability -- not that I found anyway (plus it runs terribly slow on my system).  The Windows version might so you could try running it through Wine if you aren't comfortable with using Mednafen.

---

### Post by disturbedite on 2008-05-27
i had moderately good performance with vba on linux but on windows the performance was absolutely blistering.  don't know exactly what the difference in performance was caused by...

---

### Post by DoktorSeven on 2008-05-27
The difference is the Linux version apparently does not use direct screen rendering to the videocard to speed up drawing and refreshing the emulated screen, unlike the Windows version (that probably uses DirectDraw which utilizes the videocard).  Most Linux emulators lately use an OpenGL surface to achieve this -- not that it's drawing anything in 3d, just that it's using an accelerated surface to draw on to speed things up.

---

### Post by arfink on 2008-05-27
Yeah, to get good performance in mednafen, which is very fast on my machine, you will want to open up the config file and change some things. You can find the config file in /home/username/.mednafen

Scroll down a bit until you find a place where you can change from openGL mode to SDL mode. Also, to prevent skipping in the sound I have found it's nice to set the audio rate to 48000. Also, turn off Vsync and if your machine is very slow turn on frame skip. And if you like to use the "fast forward" key like I do (skipping dialog in RPGs, etc.) then you should make it mute the audio during fast forward to prevent it from "garbling" when you go back to normal playing speed. 

One easy way to handle GBA games, if you want to use a wee bit more HDD space- unzip the game, and you will see it has an extension of ".gba"  You can then right click and choose "open with" and then type the word "mednafen" into the command box. Now you don't need a frontend, just browse to the rom you want and double click. Viola!

---

