---
title: "Line In Question"
date: 2007-06-13
forum: Dell  Ubuntu Support
---

### Post by ScottLij on 2007-06-13
I'm trying to run the audio from one PC through a E520 N with Feisty installed.  When I hook it up I'm not hearing sound from the PC but the sound from the 520 works.  Do I have to enable the line in through Feisty somehow?

---

### Post by angryfirelord on 2007-06-20
Open up a terminal and type **alsamixer**. Look for something called Line and turn it up. If that doesn't work, then fiddle with some of the settings in there and see if that does anything.

---

### Post by ScottLij on 2007-06-20
Ok, I've tried to change these settings before in a GUI setting but it doesn't seem to get it to work.  When I type alsamixer in the terminal it brings up a text based GUI.  In this it has an option of line in but I can't turn it up or down like I can other options on the page such as Surround, Center, LFE, Side, etc.  Do I want "Line in as output" on or off?  I can't seem to get any sound to play through the line in port.  I've tested all the cables and ports so I know it isn't a problem with the connections.

---

### Post by neptho on 2007-06-21
> **ScottLij said:**
> I can't seem to get any sound to play through the line in port.

You are trying to get sound input into your computer, yes?  The Line In is an input port, and the Intel HDA driver in ALSA is generally Simplex.

This means you can only play or record at a single time.  Try using Audacity to record from line in and then play it back.  :)

---

