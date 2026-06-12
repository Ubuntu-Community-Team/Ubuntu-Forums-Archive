---
title: "howto enable &quot;VT100 Special Key Codes&quot; in terminal"
date: 2009-01-08
forum: General Help
---

### Post by cb951303 on 2009-01-08
Right now, when I press the key 8 from keypad it writes 8 (key code 0x) to the screen. What I want it to do is echo <ESC>8 (key code \eOx). From what I understand it should be the default behaviour for a vt100 compatible terminal emulator anyway. 

[http://ascii-table.com/ansi-escape-sequences-vt-100.php](http://ascii-table.com/ansi-escape-sequences-vt-100.php) look at the bottom of the page for ref.

Thanks

Edit: I tried with gnome-terminal and xterm

---

### Post by cmnorton on 2009-01-09
I had to purchase a Linux terminal emulator to accomplish this. There's a very nice open source java terminal emulator, but it was not fully functional. If you want this on Linux, Power Term Interconnect for Linux from Ericom is good. If for Windows, VanDyke's SecureCRT is quite good.

If you find an answer, I would be post interested in hearing it.

---

### Post by cb951303 on 2009-01-09
maybe a system wide keyboard layout can solve this?
I looked at gnome setting and there are lot of keypad compatiblity settings there but none of them works as a vt100 keypad.

Thanks for info, but I refuse to pay for an terminal emulator :D (If your work depends on it, its quite understandable though)

---

### Post by cmnorton on 2009-01-09
You might be able to doctor up /etc/terminfo and then set that in your environment.

---

### Post by cb951303 on 2009-01-09
Ok I found out that what I'm looking is called VT102/VT220 mode. And from what I read I'm pretty sure that a lot of terminal emulators are capable of doing it including gnome-terminal. It's supposed to be done via $TERM environment variable. Anyone knows anything about it? I can't find any info...

Thanks

---

### Post by cb951303 on 2009-01-09
another update: 

I need to set the TERM env to "vt220" but gnome-terminal overwrites it everytime I open it. Is there a way to prevent gnome-terminal change the value of TERM env?

thanks

EDIT: Turns out TERM env is only for applications to understand on what type of terminal they work. It's not an emulation switch.

For future reference: I solved my problem by using Xterm in VT220 emulation mode. Ctrl + Right Click brings the menu. Just switch on the VT220 and voila!

---

