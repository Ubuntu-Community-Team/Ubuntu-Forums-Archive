---
title: "Spectrum Emulator - Speccy 1.6 Question"
date: 2009-01-17
forum: Gaming &amp; Leisure
---

### Post by Rytron on 2009-01-17
Hi,
I came across this Speccy 1.6 emulator:

Downloads:
[http://fms.komkon.org/Speccy/#Downloads](http://fms.komkon.org/Speccy/#Downloads)

Manual:
[http://fms.komkon.org/Speccy/Speccy.html](http://fms.komkon.org/Speccy/Speccy.html)

I press F4 and it brings up a menu. Then I select a game and hit enter. Then nothing happens. What must I do?

---

### Post by Grishka on 2009-01-17
if the game is not in a snapshot format (.sna), then it's a tape file. so you need to load a tape in the emulator. this is accomplished by entering LOAD "" (press J for LOAD) at the BASIC prompt, or using the tape loader in Spectrum 128k mode.

---

### Post by Rytron on 2009-01-18
Thanks. I loaded a .sna file and it worked immediately. Also the .z80 games worked immediately. Only one game so far has sound(enduro racer.z80). I have yet to get my game pad working with any game.
I could not load either .tap or .tzx files. How do I get to the basic prompt?

---

### Post by Grishka on 2009-01-18
> **Rytron said:**
> Thanks. I loaded a .sna file and it worked immediately. Also the .z80 games worked immediately. Only one game so far has sound(enduro racer.z80). I have yet to get my game pad working with any game.
I could not load either .tap or .tzx files. How do I get to the basic prompt?

I don't know about a game pad, perhaps you can get it to emulate a Kempston joystick, but most games can be played with a keyboard. maybe you can map your gamepad to some keys or something. Spectrum uses a special version of BASIC programming language, it can be used to write simple programs, and to give commands to a Spectrum computer. it's unique, because commands are mapped to certain keys. for example pressing "P" will result in the "PRINT" command. the original ZX Spectrum (the 48k model) accepts commands right after booting. ("© 1982 Sinclair Research Ltd" appears on the screen) so simply press "J" for "LOAD" then enter two quotes (""). so it will look like LOAD "". then simply press enter. this will start loading from the tape.

---

