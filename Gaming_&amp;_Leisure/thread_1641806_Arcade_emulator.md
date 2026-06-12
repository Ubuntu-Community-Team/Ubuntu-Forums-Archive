---
title: "Arcade emulator"
date: 2010-12-09
forum: Gaming &amp; Leisure
---

### Post by Donalt2010 on 2010-12-09
Is there an emulator out there for Ubuntu that plays the old Killer Instinct arcade game out there?:popcorn:

---

### Post by thatguruguy on 2010-12-09
Mame

---

### Post by Donalt2010 on 2010-12-09
Cheers. Do you know if K.I arcade works on it?

---

### Post by amauk on 2010-12-09
mame is what you want
the multiple arcade machine emulator
It's in the repositories

However, the legality of roms for arcade games is dependant on the country you're in

---

### Post by Donalt2010 on 2010-12-09
Cheers downloading now. Yea i know all the legality's of it, well sort of lol.:)

---

### Post by Donalt2010 on 2010-12-09
got the files but cant seem to get them to work with gmame:( files not found

---

### Post by amauk on 2010-12-09
The way arcade cabinets work is a bit strange

Often, a game will be released in a cabinet, then later other variants of the game appear

variants may differ in:
- The language used
(many games are developed by japanese companies, so varients are produced for other languages)
- Minor gameplay changes
- Sometimes the cabinet hardware changes as well, so different variants may deal with cabinet hardware changes

Seeing as roms are direct data dumps of arcade machines, all these things are reflected in roms as well

Often on rom sites, you'll find one version of the game that is quite large (x megabytes)
and several smaller sized variants (x kilobytes)

This large version is the original game (original gameplay, language and cabinet hardware)
the smaller files are the variants

The variants depend on the original game (and possibly depend on other variants as well, some games have gone through many variants)

It can be a little complex to work out
but mame does a good job of telling you what you need and if anything's missing

All roms are stored in zip files
Start off my making sure you have the original game (basically the biggest file)
then get the variant you want
99% of the time, this will be ok
but if you still get missing files, download all the game variants you find, and look in the zip files for the missing files - find them, then this variant is a dependency of the variant you want

Btw, don't unzip stuff
Mame needs everything kept in zip files

---

### Post by Donalt2010 on 2010-12-10
The only file i am missing is the 95mb one from the .zip file, the rest are there, but ive got the chd file seperately which is 95 mb. Grrrrr such a melt!

---

### Post by mips on 2010-12-10
Try using SDLMame instead. I've also got issues with Gmame not listing all files.

---

### Post by Donalt2010 on 2010-12-10
Got it just hope it works

Cant seem to find it now, does it need gmame installed aswell?

---

### Post by Donalt2010 on 2010-12-10
I give up:(

---

### Post by mips on 2010-12-10
> **Donalt2010 said:**
> Got it just hope it works

Cant seem to find it now, does it need gmame installed aswell?

Synaptic says the dependancies for sdlmame & sdlmane-tools are mame & mametools.

---

### Post by amauk on 2010-12-10
SDL-Mame used to be a fork of Mame that used the SDL libraries for graphics & input

SDL-Mame doesn't exist anymore
It's just Mame

The main trunk of Mame moved over to using SDL by default

Mame is a command-line program
You launch it with a rom name as an argument

The reason for being CLI only, is it's then easy to integrate Mame into other programs (Eg. MythTV)

There are various graphical front-ends to Mame
One is gmameui
These front-ends give you a graphical way to run Mame

Install mame and gmameui
GMAMEUI will be in the Applications menu

---

### Post by Donalt2010 on 2010-12-10
Ive got them all installed, i think the problem im having is when i try to open the game i get told that the files (_all of them_ cant be found) I do have them all, i think i just am having problems of where to put the files ive got mine set up in my directories option as MAME executables : /usr/games/mame and ROM : /home/donal/desktop is that right or do they need to be put somewhere else?

---

### Post by amauk on 2010-12-10
The Roms folder needs to be set to the directory containing all the roms

I'd put them all in a folder called "roms" in your home folder, then set the roms folder in GMAMEUI to point to that folder

---

### Post by Donalt2010 on 2010-12-10
I'm just after trying that its still saying files not found even though all the files are there. Strange.

---

### Post by amauk on 2010-12-10
and all the roms are in their original zip files?
(Ie. you haven't unzipped them?)

---

### Post by Donalt2010 on 2010-12-10
the chd file (the big file) didnt come zipped, but the rest are zipped, ive now got the directory set as /home/donal/roms (roms the folder i created in the home folder)?

---

### Post by mips on 2010-12-15
In Gmameui go to Options->Directories->MAME Main Paths->ROMs and "Add" a path to your ROM folder and click "Close". 

Back in the main window of Gmameui click on the circular "Reload" icon just below "Options", it should now scan the directory you specified and build a ROM database which will be displayed as a listing in the main window.

---

