---
title: "xterm over serial link?"
date: 2010-02-08
forum: Desktop Environments
---

### Post by size_XXM on 2010-02-08
I'm looking for a program (or a way to use existing programs) to connect to another linux machine over serial port and have an xterm console - basically what I get when I connect over ssh. So far I've tried minicom and putty, which only emulate vt100, and gtkterm which appears to emulate xterm, but fails with scrolling up in less or man. Is there a way to get a fancy color-enabled, resize-able, scrollable terminal console over serial link? Or maybe a way to hook xterm itself to a serial port?

TIA for any helpful advice ;)

---

### Post by size_XXM on 2010-02-09
I've managed to narrow down the problem:
Screen (as in *GNU Screen*) can apparently work with serial ports:
$ screen /dev/ttyUSB0 [flags..]
The optional flags are for setting speed, start/stop bits, parity and possibly flow control. Google/see manual for more, all I needed to set was speed.
It's apparently not possible (yet?) to automatically tell the remote machine when the console screen is resized. I have to determine my console size - Konsole displays the size when its window is being resized, alternatively there's *$ stty -a* to print all setting of the current console - this needs to be run on the local machine of course ;). Then I run *$ stty cols <x> rows <y>* on the remote machine and fullscreen apps such as aptitude, less work flawlessly :)

---

