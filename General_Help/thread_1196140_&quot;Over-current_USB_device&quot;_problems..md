---
title: "&quot;Over-current USB device&quot; problems."
date: 2009-06-24
forum: General Help
---

### Post by Marlonsm on 2009-06-24
I don't think this problem is related to Ubuntu, but as this is the best tech-related forum I know, I think you might be able to help me again.

My computer is about 2 years old and never has had any serious problems, I think this one might be the first.

Yesterday, after no updates nor changes, the computer (on Ubuntu Jaunty) started freezing randomly for a few seconds, I've hit Ctrl+Alt+F1 to get to the terminal and know if something was possibly wrong, and here is what I get:
[[IMG]http://img359.imageshack.us/img359/3551/p240609160601.th.jpg[/IMG]](http://img359.imageshack.us/i/p240609160601.jpg/)

Lots of "over-current change on port 7/8" and more coming every second.

I reboot the computer and when turning on, before even getting to Grub, I get this:
[[IMG]http://img354.imageshack.us/img354/6427/p2306092040.th.jpg[/IMG]](http://img354.imageshack.us/i/p2306092040.jpg/)
So I wait for it to turn the computer off and change the USB ports my printer and my mouse are on (the only things I have on USB).
When I turn it on again I get an error message about a possible failed overclock (I've never overclocked), I pressed F1 and it resumed the boot normally.

Back to Ubuntu, after some use, it started freezing again, I got to the terminal, but there was nothing there. I typed lsusb and here is what I got:
[[IMG]http://img354.imageshack.us/img354/4387/p2306091924q.th.jpg[/IMG]](http://img354.imageshack.us/i/p2306091924q.jpg/)

And it happened some three times since yesterday.

I suspect the problem is my PSU (a cheap one, BTW).

What is happening?

I tried Googleing, but everyone that got that problems was trying to overclock, but my computer is running at the very same clocks it was 2 years ago.

BTW, sorry for the picture quality, the only camera I had nearby when it happened was my cellphone.

---

### Post by Chris Musampa on 2009-06-24
It could be your PSU as you suspect, it could also be your motherboard or one of your USB devices.  Obviously the USB devices are the easiest to eliminate so I would try removing your printer and mouse and see of the problem persists.

---

### Post by niteshifter on 2009-06-24
Hi,

As Chris said disconnecting the mouse and printer is first step. I'll go a bit further and remind you to disconnect them at the computer end (printer cable). It can be the cable. Plug them in one at a time.

Another thing comes to mind: You might want open the box and have at it with a vacuum - you'd be surprised at what dust can accumulate in 2 years. While it's opened pull and re-plug - one at a time - each connector to the mobo.

---

### Post by Marlonsm on 2009-06-24
I clean my computer about once a month, so there isn't much dust in it.

But I'll try unplugging the USB devices, I've unplugged the printer now, I'll wait for some mins...

BTW, I forgot to mention on the first post: The 2 USB ports on the front of the computer rarely work anymore, I've always thought it was some problem with the computer case, but now, I think it might be related to these problems...

EDIT: It's not the printer, I've removed the mouse now.

EDIT2: Not the mouse either... I also have an USB extension plugged on one of the back ports, so I use it to plug things like pen drives, instead of using the frontal USB ports.

EDIT3: Not the extension either. I'm now on Windows XP to see if it also happens here...

EDIT4: It seems to be fixed, I got my motherboard's manual and I've seem that the USB ports 7 and 8 are the frontal ones, which weren't even working, so I've opened the computer and unplugged those ports from the motherboard.

---

