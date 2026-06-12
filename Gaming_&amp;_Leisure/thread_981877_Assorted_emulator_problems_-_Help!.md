---
title: "Assorted emulator problems - Help!"
date: 2008-11-14
forum: Gaming &amp; Leisure
---

### Post by victorcrane on 2008-11-14
Hi folks, I'm about to smash my laptop to pieces and it's all ubuntus fault. I have on dvd a vast collection of roms which I used to enjoy playing when I used windows, back in the days when things just worked...

Here's the beef....

Vice C64 emulator - installed but can't find it, anyone know how the hell you run it? 

Zsnes - Installed, crashed, crashed again, did nothing for a while, uninstalled.

Gens - Worked beautifully in hardy 8.04, doesn't seem to work at all in intrepid? 

snes9x - installed, but again absolutely no idea whatsoever how to run it. Typing 'snes9x' in terminal gives me a loooong list of what looks like some kind of configuration but that seems to be it, it just tells me everythings ok and then stops. How do I actually run the program?

Help me out folks, I keep trying to encourage my friends to try ubuntu but they all say it's a total and utter pain in the backside and a complete waste of time. I'm starting to feel like I'm going to lose the argument. :confused:

---

### Post by grossaffe on 2008-11-14
do a search for the gtk port of snes9x, it'll be much simpler than a command-line interface

---

### Post by Grishka on 2008-11-14
> **victorcrane said:**
> Hi folks, I'm about to smash my laptop to pieces and it's all ubuntus fault. I have on dvd a vast collection of roms which I used to enjoy playing when I used windows, back in the days when things just worked...

Here's the beef....

Vice C64 emulator - installed but can't find it, anyone know how the hell you run it? 

Zsnes - Installed, crashed, crashed again, did nothing for a while, uninstalled.

Gens - Worked beautifully in hardy 8.04, doesn't seem to work at all in intrepid? 

snes9x - installed, but again absolutely no idea whatsoever how to run it. Typing 'snes9x' in terminal gives me a loooong list of what looks like some kind of configuration but that seems to be it, it just tells me everythings ok and then stops. How do I actually run the program?

Help me out folks, I keep trying to encourage my friends to try ubuntu but they all say it's a total and utter pain in the backside and a complete waste of time. I'm starting to feel like I'm going to lose the argument. :confused:

VICE has different executables for different systems. run 'x64' for c64, and 'x128' for c128.
ZSNES - try this PPA: [https://launchpad.net/~roehling/+archive](https://launchpad.net/~roehling/+archive).
Gens - get Gens/GS from here: [http://info.sonicretro.org/Gens/GS](http://info.sonicretro.org/Gens/GS).
Snes9x - get the GTK version from another PPA: [https://launchpad.net/~bearoso/+archive](https://launchpad.net/~bearoso/+archive).

---

### Post by dfreer on 2008-11-14
> **victorcrane said:**
> Zsnes - Installed, crashed, crashed again, did nothing for a while, uninstalled.

Use a binary that wasn't compiled using Ubuntu Intrepid's GCC 4.3.2. There's plenty of posts here on the forums about this.

---

### Post by victorcrane on 2008-11-15
Well at least I have vice and zsnes working now, many thanks indeed guys. :guitar:

---

