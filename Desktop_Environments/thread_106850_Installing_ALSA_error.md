---
title: "Installing ALSA error"
date: 2005-12-21
forum: Desktop Environments
---

### Post by Coyne on 2005-12-21
Owkey, I get following error when I install ALSA:


  [B] checking for initscr in -lncurses... no
   checking for initscr in -lcurses... no
   configure: error: this packages requires a curses library
   make: *** Geen doelen gespecificeerd en geen makefile gevonden.  Stop.(No target specified and no makefile found)
   make: *** Geen regel voor het maken van doel `install'.  Stop.(No line for making target 'install'
   rm: cannot remove `/dev/sndstat': Toegang geweigerd(Acces Denied)
   ln: `/dev/sndstat': Bestand bestaat(File exists)
   cp: cannot remove `/usr/share/sounds/alsa/test.wav': Toegang geweigerd(Acces Denied)
   Remove Folder.....
   ./install: line 89: alsaconf: command not found[/B]


Lol, this way you guys can learn some dutch too :d


Can someone help me with this ???

---

### Post by dcstar on 2005-12-21
[QUOTE=Coyne]Owkey, I get following error when I install ALSA:


  [B] checking for initscr in -lncurses... no
   checking for initscr in -lcurses... no
   configure: error: this packages requires a curses library
   make: *** Geen doelen gespecificeerd en geen makefile gevonden.  Stop.(No target specified and no makefile found)
   make: *** Geen regel voor het maken van doel `install'.  Stop.(No line for making target 'install'
   rm: cannot remove `/dev/sndstat': Toegang geweigerd(Acces Denied)
   ln: `/dev/sndstat': Bestand bestaat(File exists)
   cp: cannot remove `/usr/share/sounds/alsa/test.wav': Toegang geweigerd(Acces Denied)
   Remove Folder.....
   ./install: line 89: alsaconf: command not found[/B]


Lol, this way you guys can learn some dutch too :d


Can someone help me with this ???[/QUOTE]

I'd say you need some of the curses-dev packages on your system if you are compiling this package.

---

