---
title: "VICE C64 emulator v1.16 freezes during startup - Ubuntu hoary"
date: 2005-07-06
forum: Gaming &amp; Leisure
---

### Post by fif on 2005-07-06
Hello there,

I retrieved last version of the VICE emulator sources, compiled and installed it.

```
./configure
make
sudo make install

```


Launching the emulator (x64), I get the following message in the console and the display freezes - emulator window is opened but the emulated display remains black.

```
Welcome to x64, the free portable C64 Emulator.

Current VICE team members:
A. Boose, D. Lem, T. Biczo, A. Dehmel, T. Bretz, A. Matthies,
M. Pottendorfer, M. Brenner, S. Trikaliotis.

This is free software with ABSOLUTELY NO WARRANTY.
See the "About VICE" command for more info.

X11: Dï¿½tectï¿½ une capacitï¿½ visuelle de 24bits/TrueColor.
X11: Utilisation d'un "colormap" privï¿½.
Loading system file `/usr/local/lib/vice/C64/kernal'.
C64MEM: Kernal rev #3.
Loading system file `/usr/local/lib/vice/C64/basic'.
Loading system file `/usr/local/lib/vice/C64/chargen'.
Loading system file `/usr/local/lib/vice/PRINTER/mps803'.
Palette: Loading palette `/usr/local/lib/vice/PRINTER/mps803.vpl'.
Loading system file `/usr/local/lib/vice/PRINTER/nl10-cbm'.
Palette: Loading palette `/usr/local/lib/vice/PRINTER/mps803.vpl'.
NL10: Printer driver initialized.
Loading system file `/usr/local/lib/vice/DRIVES/dos1541'.
Loading system file `/usr/local/lib/vice/DRIVES/d1541II'.
Loading system file `/usr/local/lib/vice/DRIVES/dos1570'.
Loading system file `/usr/local/lib/vice/DRIVES/dos1571'.
Loading system file `/usr/local/lib/vice/DRIVES/dos1581'.
Loading system file `/usr/local/lib/vice/DRIVES/dos2031'.
Loading system file `/usr/local/lib/vice/DRIVES/dos2040'.
Loading system file `/usr/local/lib/vice/DRIVES/dos3040'.
Loading system file `/usr/local/lib/vice/DRIVES/dos4040'.
Loading system file `/usr/local/lib/vice/DRIVES/dos1001'.
Drive: Finished loading ROM images.
X11Video: Initialisation rï¿½ussie, avec mï¿½moire partagï¿½e.
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset
X11Video: Initialisation rï¿½ussie, avec mï¿½moire partagï¿½e.
Keyboard: Loading keymap `/usr/local/lib/vice/C64/x11_sym.vkm'.
Joystick: Initialisation de l'interface des joysticks de Linux...
Joystick: Warning - Impossible d'ouvrir le pï¿½riphï¿½rique joystick
`/dev/input/js0'.
Joystick: Warning - Impossible d'ouvrir le pï¿½riphï¿½rique joystick
`/dev/input/js1'.
Main CPU: starting at ($FFFC).
Main CPU: RESET.
Drive 8: RESET.

```

Thinking that the warning on usable font sets could be the problem, I tried with a chargen file that was working fine with the Windows version of the emulator but problem remains. Checking with x128 also gives the same issue.

Does anyone have a clue?

---

### Post by fif on 2005-07-06
Problem was due to the lock of the audio resources.
```
esddsp x64
```
Emulator starts correctly with full sound.
Next search is to be able to have it fullscreen (need to check how to configure the makefile appropriately)

---

