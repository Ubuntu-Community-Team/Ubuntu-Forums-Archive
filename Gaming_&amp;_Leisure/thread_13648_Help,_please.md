---
title: "Help, please"
date: 2005-02-02
forum: Gaming &amp; Leisure
---

### Post by Cecil on 2005-02-02
OK, I'm trying to get the emulator zsnes to work. I compiled the sources just fine, but when I double-click on the binary, nothing happens. When I try running it from the command line, I get the error "Could not set 512x448 video mode: No available video device" I think this means there's something I have to install, but I don't know what. Here's my computer specs, in case you need them.

Intel Celeron 1.3GHz
512MB PC133 SDRAM
ASUS ATI Radeon 7000 64MB DDR

I tried installing the ATI drivers before, but that caused Xfree to refuse to start. I ended-up re-installing Linux.

---

### Post by dhonn on 2005-02-02
Most computers don't support that native videomode.  especially if you have an LCD. Run the zsnes command in the terminal but add the line --help so you can get someoptions to change to video mode.  a nice standard mode would be 640x480.  I think it should work from their.  Also try looking for a gui companion to zsnes.

---

### Post by Cecil on 2005-02-02
OK, I managed to find the configuration files for zsnes. No matter what resolution I try to have zsnes start in, I get an error message (if I'm using the command line). If it's any openGl mode, say 640x480 ogl, I get the message, Cannot set 640x480-GL video mode. And it doesn't matter what resolution. If it's not an openGl mode, I get the same message from my first post, regardless of resolution.

---

### Post by valadil on 2005-02-02
Try telling it to run in a window instead of full screen.

Conversely you could try adding whatever resolution zsnes wants to your x11 config file.

---

### Post by Cecil on 2005-02-02
[QUOTE=valadil]Try telling it to run in a window instead of full screen.

Conversely you could try adding whatever resolution zsnes wants to your x11 config file.[/QUOTE]I've tried both windowed and full screen modes. And, could you tell me how to edit the x11 config file?

Edit: I'm wondering, is there a version of the fglrx driver for a RADEON 7000 that I need to install? I have the RADEON 7000 driver installed already, but I don't have the fglrx driver installed.

---

