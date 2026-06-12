---
title: "paste is SHIFT-INSERT, what's copy?"
date: 2013-09-10
forum: Desktop Environments
---

### Post by jdl2 on 2013-09-10
Does Ubuntu 12.04 have any key combinations that will copy selected text from an xterm window into a buffer? Since my right-click menu is missing in xterm, I'd like to select text and copy it to a buffer by pressing a key combination. Is there an easy way to do this? If it involves remaping the keys, will you please provide detailed instructions since I'm new to key remapping, configuring the desktop, etc.

Thank you,

jdl

---

### Post by TheFu on 2013-09-10
Inside a pure Xterm, the mouse is all you need, no keyboard anything.  It uses the X-buffer, not a clipboard like Windows.

The action is 
* select using the left mouse button
* paste using the center mouse button

Much easier than using a keyboard.  Most X/Windows apps honor this method, but a few do not - they actively have to ignore the X/Windows x-buffer for this.  Firefox and Thunderbird are the ones that I notice most.  Oh and this only works for text, not images or other data types.

---

### Post by vrih on 2013-09-11
CTRL-INSERT seems to work in most situations for me as a copy.

---

### Post by jdl2 on 2013-09-11
Thank you both!!!! CTRL-INSERT works great! I don't have a 3 button mouse but I'll try to map my Kensington Expert Mouse to simulate a 3rd mouse button.

---

### Post by TheFu on 2013-09-11
> **jdl2 said:**
> Thank you both!!!! CTRL-INSERT works great! I don't have a 3 button mouse but I'll try to map my Kensington Expert Mouse to simulate a 3rd mouse button.


Clicking both mice buttons concurrently simulates the 3rd/middle button. It is picky, so be certain to press both L/R buttons simultaneously.

---

