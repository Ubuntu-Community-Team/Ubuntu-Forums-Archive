---
title: "PS1 emulators in ubuntu"
date: 2009-07-02
forum: Gaming &amp; Leisure
---

### Post by jhedd on 2009-07-02
How can I install PS1 emulators in ubuntu? Any ideas? :lolflag:

---

### Post by K.Y.A on 2009-07-02
Click applications >> add/remove. Then, search for pcsx. Check the box on what comes up and click apply. This will install the emulator, I AM NOT RESPONSIBLE FOR ANY LEGAL MATTERS.

---

### Post by jhedd on 2009-07-02
Will it worked? How about the roms? Is it the same roms using in windows?:lolflag:

---

### Post by mitanka on 2009-07-02
Yes, you can use the same roms from windows version of ps1 emulator. I already play some ps1 games on Ubuntu 9.04 with much better results than on Windows XP

---

### Post by hikaricore on 2009-07-02
Do not discuss "roms" or cd isos here..

---

### Post by hessiess on 2009-07-03
Don't use PCSX, it is no longer developed. pSX is a much better/easier to use emulater. epsxe is also good once you work out how to get it running (damn plugins...).

---

### Post by BoyOfDestiny on 2009-07-03
The pcsx packaged in Ubuntu is pcsx-df.
[http://pcsx-df.sourceforge.net/](http://pcsx-df.sourceforge.net/)

A new version came out a little over a month ago. 

It is Free Software, runs on multiple architectures and to top it off, does not require a Sony PlayStation BIOS as it has it's own implementation (although it can use the BIOS if you have one.)

It is easy to configure with it's GUI, and doesn't take more than a couple of minutes to set up (assuming you have a gamepad you need to configure...) 

I can't comment on the proprietary emulators, as I've never tried them, but pcsx-df isn't hard to use.

---

### Post by ShadowTek on 2009-07-03
> **hikaricore said:**
> Do not discuss "roms" or cd isos here..
What if the ISO was made from a legitimately purchased disk that the poster made himself, and he just wanted advice regarding how to use it properly?

---

### Post by zero777zero on 2009-07-03
last time i checked pSX still has a sound issue with ubuntu

---

### Post by ShadowTek on 2009-07-04
> **zero777zero said:**
> last time i checked pSX still has a sound issue with ubuntu
I usually have to do a **sudo killall pulseaudio** before I start pSX, otherwise I'll get a segmentation fault. Other than that, I haven't noticed any real sound problems while playing Metal Gear Solid.

I *have* noticed some popping from one of my speakers during certain cinematics, but I'm pretty sure that's due to that speaker being slightly blown.

---

### Post by zero777zero on 2009-07-04
i'd say the need to kill pulseaudio is a pretty significant problem

---

### Post by Grishka on 2009-07-04
> **zero777zero said:**
> i'd say the need to kill pulseaudio is a pretty significant problem

the commands are simple, and there are no side effects for the system. I'd say you're exaggerating. see [this thread](http://ubuntuforums.org/showthread.php?t=1169703). also, seeing that pSX is closed source, and unmaintained, this will only get worse in time. enjoy it while you still can.

---

### Post by BigSilly on 2009-07-05
[Looks like a new pSX could be with us soon.]("http://psxemulator.proboards.com/index.cgi?board=general&action=display&thread=3138&page=1#26729")

---

### Post by Bonzai11 on 2009-07-05
Just wondering so Psx is a better alternative to pcsx?
Settin up Psx right now a little work but it will definitely be worth it.

---

### Post by ShadowTek on 2009-07-05
> Just wondering so Psx is a better alternative to pcsx?
PCSX wouldn't work for me on 8.10 *or* 9.04, so that's why I'm using pSX.

---

### Post by zero777zero on 2009-07-05
> **Grishka said:**
> the commands are simple, and there are no side effects for the system. I'd say you're exaggerating.

i consider the need to remember terminal commands for an emulator, and using them everytime i want to play an emulator a bit of a thorn in the side. btw, what is the command to restart pulse audio without rebooting?

---

### Post by Grishka on 2009-07-06
> **zero777zero said:**
> i consider the need to remember terminal commands for an emulator, and using them everytime i want to play an emulator a bit of a thorn in the side. btw, what is the command to restart pulse audio without rebooting?

I don't have to do anything every time I start pSX. I just had to kill pulseaudio, run pSX as root, set the correct audio device in the settings, and copy the device string to psx.ini in my home folder. all of this just once. then pSX works for me without hassle even after system reboot. no further meddling with pulseaudio should be needed.

---

### Post by hessiess on 2009-07-06
> **zero777zero said:**
> i consider the need to remember terminal commands for an emulator, and using them everytime i want to play an emulator a bit of a thorn in the side. btw, what is the command to restart pulse audio without rebooting?

If its that much of a problem just make a shell script.

---

