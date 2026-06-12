---
title: "nVidia now has bad colours"
date: 2007-12-10
forum: Desktop Environments
---

### Post by nick4mony on 2007-12-10
Hi.

I've had Gutsy and Win XP working on my machine for about 3 months, but now a strange issue came up twice in one day: one second the display is fine, next second the display goes funny (looks grainy and pink).  I reboot to Windows XP and the same issue shows up there, too.

The first time, an I.T. techo from desktop support came and installed an extra driver into Win XP, and that cleared the problem in both Windows and Gutsy.  It's happened again, very close to the end of the day.

I can't understand this at all, because if it was a software issue, it would occur only on one O.S. and if it was a hardware issue, it wouldn't be fixed by a software driver.  

Anybody got any ideas for a cause, or things to try?

**More detailed symptoms:**
[list]
[*] On a grey scrollbar, there are vertical red/pink lines.
[*] On a colour gradient (like the Ubuntu background) it looks grainy.
[*] On a white or grey background it looks pink.
[*] Screen resolution hasn't changed, and it is still workable, but I wouldn't like to keep going for a long time.
[*] I don't want to reboot to reinstall the driver twice a day, that would be a drag.
[/list]

**It happened when ...**
[list]
[*] (first time) I had turned away from the computer to work on some papers (it hadn't triggered the screen saver).
[*] (second time) While I was actually using the computer - I actually saw it happen - during a 2-3 second pause for both mouse and keyboard.
[/list]

**Hardware details**
[list]
[*] Graphics card is nVidia GeForce PCX5750, with 128MB memory, BIOS ver 4.36.20.38.00, DAC type Integrated RAMDAC - wtm (whatever that means).
[*] Monitor is a Samsung SyncMaster 940B, using a DVI connector
[*] I've unplugged and replugged everything (DVI, Power, keyboard, ...) but haven't been inside the computer.
[*] Using Gutsy 7.10 - at the time I was using the Restricted Driver, with extra visual effects (background -> RMB -> Chg Desk Bgnd; then Visual Effects -> Extra).
[/list]

**I've tried ...**
[list]
[*] Ctrl-Alt-F1 then Ctrl-Alt-F7.  I must say the console font doesn't look too good either.
[*] Reboot (several times), including completely removing power from computer and monitor for 2-3 minutes.
[*] Go into Windows, looks bad there, too.  Even grub and the various spash screens don't look normal either.
[*] Change screen resolutions (no effect).
[*] The IT techo installed an nVidia driver in Windows, which cleared the problem for **both** operating systems (**that's the bit I can't figure out**)
[*] Took a screen shot - but viewing the screenshot on someone else's machine looks perfectly normal, so I can't show you what it looks like.
[*] I disabled the Restricted nVidia driver.  No effect (yet).
[/list]

Ideas?

---

### Post by ske1fr on 2007-12-10
The fact that the colour cast happens towards the end of the day suggests that it's a physical hardware problem. Some part of the signal path  is changing electrical conductivity like a dry solder joint.  Interesting that the Windowws driver resets the output card both in Windows and Ubuntu.   

Cultivate your IT technician and ask for a swapout of the graphics card - see if the replacement exhibits the same behaviour.

---

### Post by nick4mony on 2007-12-10
> **ske1fr said:**
> The fact that the colour cast happens towards the end of the day suggests that it's a physical hardware problem.

Err, the first time was near the beginning of the day, about 1 hour after I turned the machine on [size=-2](I know it's not my electricity, but the cost of it is **doubling** in Melbourne - hence I turn it off overnight)[/size]. The second time was near the end of the day.

> Interesting that the Windowws driver resets the output card both in Windows and Ubuntu.
I agree, that's the crux of the whole puzzle. :confused:

> Cultivate your IT technician
what? Cultivate like a mushroom? :biggrin:

---

### Post by nick4mony on 2007-12-11
An update: Just after lunch today, the problem went away by itself.  This is starting to look more like a hardware issue (still, the windows driver update business is freaky :-k ).  I'm in Gutsy at present, I'll know for sure when I boot later on into Grub and Win XP, but the Ctrl-Alt-F1 console font looks better, 

I reckon if it happens again, I'll try reseating the graphics card.

N.

---

