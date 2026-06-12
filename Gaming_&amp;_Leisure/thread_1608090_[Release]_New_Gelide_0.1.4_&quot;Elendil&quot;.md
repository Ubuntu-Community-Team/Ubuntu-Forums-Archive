---
title: "[Release] New Gelide 0.1.4 &quot;Elendil&quot;"
date: 2010-10-28
forum: Gaming &amp; Leisure
---

### Post by gelide on 2010-10-28
A year and a half later, here we are with a new version of [Gelide: 0.1.4 "Elendil"]("http://gelide.sf.net").
Hope you like!

Full list of changes for the 0.1.4 release of Gelide FrontEnd for GnuLinux:

* New and updated:
- A new search system has been developed. Now it is case insensitive and allow you to use the most standar wildcards:
[INDENT]"*" for replacement of zero or more characters.
"?" for replacement of exactly one character.[/INDENT]
- The pannels of systems and emulators have been modified. Now you can move your systems or your emulators inside their pannels. 
- A new DAT file system has been developed with support for three diferent DAT formats:
[INDENT]ClrMamePro.
Mame XML (You can get a dat file with "mame -listxml").
Logiqx XML.[/INDENT]
- The games list generator has been revised. Now with two options in the configuration dialog, you can decide whether to keep the current data of your games (favorites, rank, etc.) and also you can decide if you want to add games that are not in the DAT file (unknown games). 
- The Libglade dependency has been removed. 
- A new configuration system based on XML files, lets us remove the dependency with Gconf. Now Gelide only rely on libgtkmm and libxml2. 
- The emulators launcher has been revised. Now with an option in the configuration, you can decide when to keep open the launcher dialog after the emulation. 
- Added "Nintendo DS" to the systems list with the emulator DeSMuME preconfigured. 
- Added "SEGA 32X" to the systems list with the emulators Gens/Gs, Mess and SdlMess preconfigured. 
- Added "SNK Neo Geo Pocket" to the systems list with the emulators Mednafen, Xe, Mess and SdlMess preconfigured. 
- Added "SNK Neo Geo Pocket Color" to the systems list with the emulators Mednafen, Xe, Mess and SdlMess preconfigured. 
- The preconfiguration of MESS emulator has been added for virtually all systems. 
- The preconfiguration of MAME emulator has been added for arcade systems. 
- Added the preconfiguration of z26 emulator to "Atari 2600" system. 
- Added the preconfiguration of Handy/SDL emulator to "Atari Lynx" system. 
- Added the preconfiguration of Nestopia emulator to "Nintendo FDS" and "Nintendo NES". 
- Added the preconfiguration of "Gngb and Gnuboy to "Nintendo Game Boy" and "Nintendo Game Boy Color". 
- Added the preconfiguration of BoyCott Advance-SDL to "Nintendo Game Boy Advance". 
- Added the preconfiguration of Bsnes y SNes9x-Gtk to "Nintendo SNES". 
- Updated the preconfigurations of SdlMess, SdlMame, Stella, Mednafen, Xe, FCEUX, Raine, Gens/GS, Osmose and Generator 
- These emulators have been removed: FCEU, Snes9x and Dgen/Sdl. 
- The document "Systems&Emulators-HowTo.es_ES.txt" has been rewritten, now includes much more information and documentation on the systems and emulators configured in Gelide at the current version (Sorry, only in Spanish at this moment, would you like to translate it? contact me at gelide.prj AT gmail DOT com). 
- Updated French translation of Gelide by Emeric Grange (Thank you for contributing).
- Updated Swedish translation of Gelide by Daniel Nylander (Thank you for contributing).
- Updated Spanish translation.

* Fixes: 
- Bug in the Information Pannel. Now, images are correctly scaled when entering / leaving fullscreen mode and also when main window is maximized or minimized. 
- Bug in the command line that prevented the proper use of paths with spaces in the emulators' executables. 

As for the web, we have restructured the content and created a few new sections. Inside the Downloads section, we have created a new section intended to add DAT files for each of the systems supported by Gelide. We also added a link to the forums of the project in which the registration is NOT required to make use of them. Besides all this, we want to document Gelide completely, so we've created a Help section in which we will try to put all the documentation we can.

You can download it from [http://gelide.sf.net]("http://gelide.sf.net")

Greetings: jamf

---

