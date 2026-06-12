---
title: "Need help with USB-&gt;RS232(DB9)-&gt;Genesis controller"
date: 2009-10-07
forum: Gaming &amp; Leisure
---

### Post by nssone on 2009-10-07
I have a USB-RS232 (9 pin connector) and I'm trying to find a way to use it as a joystick/controller for Kega Fusion. Problem is, I can't really seem to find any kind of drivers for this. I know that my kernel should have something like this already installed in it, and it shows up under ttyUSB0. But from there I'm lost.

Is there anybody out there willing to help me out? I really wanted to use this as a cheap alternative to a HID that would've cost me 5x more than this cost. And it's not as difficult in Windows and it seems to be here. Yeah, I know, it would've been less hassle, but I wanted to save a few bucks and I used to have more fun doing things this way. So if anybody is willing to help, I'll fully comply as I would really like to try and get this going.

Thanks.

---

### Post by GerbilSoft on 2009-10-08
I don't think you can use a USB Serial adapter for Sega Genesis controllers on any operating system. RS-232 uses a completely different protocol; among other things, it uses two lines for data transfer (send and receive), and voltage is -12V/+12V. The Genesis controller uses several lines for controls and uses TTL signalling (0V/+5V).

If you did actually get a Genesis controller working with a serial port, I'd like to know how you did it.

---

