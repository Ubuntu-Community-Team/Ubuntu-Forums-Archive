---
title: "VBA Express - sound problems"
date: 2008-04-29
forum: Emulators
---

### Post by iHurrr on 2008-04-29
I'm trying to play a game on VBA Express (a Game Boy Advance emulator). The video for the emulator runs just as it should, but the audio sounds like it's constantly being hit by a tire iron. I checked other programs, and I can hear things just fine through them (Audacious, youtube). I also checked to see if the ROM was at fault. It was not. Any ideas on what could be causing this? 


Also:
The emulator will also lock up once I close out of it. Although it's not too big of a deal (I just kill the process when I'm done), any help would be greatly appreciated.

---

### Post by erginemr on 2008-04-29
Cheesy attempt for a solution maybe, but I am using an ALSA sound config file (.asoundrc) that fixed my sound problems in the ZSnes emulator.
[http://ubuntuforums.org/showpost.php?p=4177459&postcount=9](http://ubuntuforums.org/showpost.php?p=4177459&postcount=9)

It might help...

---

### Post by iHurrr on 2008-04-29
> **erginemr said:**
> Cheesy attempt for a solution maybe, but I am using an ALSA sound config file (.asoundrc) that fixed my sound problems in the ZSnes emulator.
[http://ubuntuforums.org/showpost.php?p=4177459&postcount=9](http://ubuntuforums.org/showpost.php?p=4177459&postcount=9)

It might help...

That's incredible! It worked! Thank you so much! I've still got a lot to learn about linux, it would seem. Thanks again!

---

### Post by erginemr on 2008-04-30
You are welcome retro-gamer boy! (Me, too ;)) Take care.

---

### Post by zizzdude on 2008-06-22
strange. instead of fixing the choppy sounds in VBA, it took out the sound. :confused:

I'm using alsa btw.

---

### Post by rayefrenzy on 2008-09-12
I know this is kind of an old thread, but that fix just made things worse (the scratchiness increased 10 fold). Any other known fixes? I think I may just try Mednafen. [http://mednafen.sourceforge.net/](http://mednafen.sourceforge.net/)

---

### Post by Sockerdrickan on 2008-09-12
Or, as I always say, you can use my GB/C emu if that's your cup of tea... :popcorn: [www.tuxemu.se.nu](www.tuxemu.se.nu)

---

### Post by Konekodemon on 2009-01-06
I can't get that file to open, well at least I can play roms now, but I can't play them on full screen, the sound still lags

---

### Post by disturbedite on 2009-01-06
i'd like to kindly recommend VBA-M. it is a project that carries on vba development.

---

### Post by fabioxxxx on 2009-06-14
wine + no$gba 2.6 worked like a charm, perfect sound , but will not load some roms...

---

### Post by huffman_tree on 2009-06-24
> **iHurrr said:**
> That's incredible! It worked! Thank you so much! I've still got a lot to learn about linux, it would seem. Thanks again!
Me too.It did work.Thanks a lot!

---

### Post by usagiakumu on 2010-09-25
Wine+VisualBoy Advance actually works well. Wine+any emulator except Dolphin and DeSmuME will certainly work better. I found the latter two to work better as they are being developed mainly open source.

---

### Post by Sockerdrickan on 2010-09-26
> **usagiakumu said:**
> Wine+VisualBoy Advance actually works well. Wine+any emulator except Dolphin and DeSmuME will certainly work better. I found the latter two to work better as they are being developed mainly open source.
No need to ressurect an old thread. But for GBA you can use VBA-M on linux.

---

### Post by mauricio.dev on 2011-01-27
I've tried using gvba with throtlle = 100%.
It worked for me. Maverick with pulseaudio sound.

---

### Post by felipeludo2011@gmail.com on 2011-10-10
Nice ! The .asoundrc file work perfectly, in my ubuntu and in debian too,  thanks !

---

