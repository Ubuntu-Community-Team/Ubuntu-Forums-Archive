---
title: "Infrared Spectroscopy"
date: 2008-08-01
forum: Education &amp; Science
---

### Post by jdwood83 on 2008-08-01
Is there any program that will operate a FTIR? I think these are generally specific programs to run specific machines, so my FTIR is a Digilab (now made by Varian) Exaclibur Series FTS 3000 MX FTIR, connected via USB (not Serial). If I can get the damn thing working--the PC that carries the Windows program is broken, and I thought maybe Linux could work it--I would be doing this for my thesis.

Again, I'm looking for a program that will operate a FTIR, not one that will analyze the data. Any help would be greatly appreciated.

---

### Post by hubie on 2008-08-02
Does the manual give you a command reference or a programmer's reference?  If the instrument talks RS232 or RS422, it wouldn't be hard to write your own acquisition program (I've done this for some of the Keithley instruments).

---

### Post by jdwood83 on 2008-08-04
If I'm understanding the RS232 and RS422 correctly, those are the pinouts, right? The machine I have runs USB.

Out of curiosity, how did you write/start your programs (in the case that I might have to write my own).

---

### Post by hubie on 2008-08-04
The instruments I interacted with used [SCPI]("http://www.scpiconsortium.org/SCPI-99.pdf") (Standard Commands for Programmable Instruments) for interaction.  It is a command language that consists of short ASCII strings you send via some sort of serial communication (such as on the RS232 or RS422 buses, GPIB, as well as USB).  If you wanted to measure, say, the DC voltage, you'd send the instrument a string such as ":meas:volt:dc?" and it would return something like "+4.5717834838E+00", etc.  A Tektronix scope might return a long series of values that would be the voltage reading for an oscilloscope trace.

Because it was such a simple interface (as I said, it was RS232), I wrote a quick QBASIC program (this was something like 10 years ago).  If I was to do it again today, I would use python and use the pyserial interface.  My guess, if your instrument uses SCPI or its own serial interface, you could use pyserial to talk to /dev/ttyUSB0 (or whatever USB device it is).

---

