---
title: "Minicom"
date: 2009-01-24
forum: General Help
---

### Post by Tan Man on 2009-01-24
I am having a problem connecting to a router when using minicom. I have to do it for a lab in school, and when I use Windows it works fine, but for Ubuntu, it doesn't show the display for commands. Is this a problem with TTY8 as my teacher had said, or is it something different? And how do I fix it?

---

### Post by The Cog on 2009-01-24
I have used minicom on Ubuntu in the past, so I know it works. There is a key to get the menu but I can't rememmber what it is. I do remember I had to set the serial port, which I think was /dev/ttyS0 (note the capital S). 

If you have a GUI, you might find gtkterm easier to get on with.

P.S. 
There's no such thing as TTY8, so I'm not sure what you mean there. But minicom works both in the consoles tty0-tty6 and in a graphical gnome-terminal.

---

### Post by Tan Man on 2009-01-24
> **The Cog said:**
> I have used minicom on Ubuntu in the past, so I know it works. There is a key to get the menu but I can't rememmber what it is. I do remember I had to set the serial port, which I think was /dev/ttyS0 (note the capital S). 

If you have a GUI, you might find gtkterm easier to get on with.

P.S. 
There's no such thing as TTY8, so I'm not sure what you mean there. But minicom works both in the consoles tty0-tty6 and in a graphical gnome-terminal.

Well I was told tty8. I don't know then. 

I use terminal to get in to it using ```
minicom -s
``` then I set the bits per second and what not, then when I try to connect it doesn't work. I am also connecting through the console port to configure the router.

---

### Post by The Cog on 2009-01-25
Ah, I installed miniom and had a look. I see that it defaults its serial port to tty8 which is probably not your serial port. As I said, your serial port is probably ttyS0 - it is on my laptop. 

minicom -s should drop you in a configuration screen. Use the up/down arrows and enter to get the serial port setup. Press a to edit the serial device and change it to /dev/ttyS0 (note the capital S). It may help to set the hardware flow control to no by pressing f. Enter to exit that page, and save as dfl (meaning default I guess).

When in minicom, **Ctrl-A Z** will get you a help page. 

As I said, you might find gtkterm easier to get on with.

---

### Post by jonlemur on 2009-01-28
If it's not too late, what I would do is have the computer up and running before you plug in the device, then after you plug it in run ```
dmesg | grep tty
``` For me, connecting a USB device that uses serial port like communication, this gives ```
[26179.192750] usb 2-2: cp2101 converter now attached to ttyUSB0
``` Yours will be quite a bit different, but there should be a "attached to tty*" section.  Whatever it is, run minicom -s and change the Serial Port Setting, Serial Device to that device.  For me, I would have had to change it to /dev/ttyUSB0.  Yours will likely be /dev/ttyS0.

---

### Post by HermanAB on 2009-01-28
BTW, rather use cutecom, since it is much less painful.

Cheers,

Herman

---

