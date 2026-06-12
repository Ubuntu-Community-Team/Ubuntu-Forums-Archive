---
title: "Weird WM/terminal problem in Hardy"
date: 2008-04-25
forum: Desktop Environments
---

### Post by Taxi on 2008-04-25
Can anybody help me with a weird window manager problem in Xubuntu Hardy?

Xfce4-terminal is opening without window decorations.  It has the right shape, but instead of the title bar, frame, close button, etc it is just solid black.  I can click where the buttons should be and they work, but they're not visible.  Window decorations on all my other apps (at least the ones I've used so far) have been fine.

Compositing is off and I've tried changing the window manager style and the theme and it's still doing it.  I also tried re-downloading and re-installing the xfce4-terminal, xfwm4, and xfwm4-themes packages in Synaptic but there was no improvement.  Does anyone have any suggestions for me?  Or has anyone had a similar problem with Hardy?

---

### Post by afoglia on 2008-04-26
I don't have any suggestions, but I too just upgraded to Hardy and have the same problem.  Someone opened a bug report on it back in February, but there's been no developments since then.

[https://bugs.launchpad.net/ubuntu/+source/xfce4-terminal/+bug/194769](https://bugs.launchpad.net/ubuntu/+source/xfce4-terminal/+bug/194769)

---

### Post by Taxi on 2008-04-26
Thanks for confirming the problem (here and in Launchpad).  I'm surprised the bug has hung around so long, but maybe it's not that common.  I jumped into the #Xubuntu channel real quick and it is definitely working properly for at least some people.

Anyway, I'm sort of glad to hear it's not just me, but I'm also sorry to hear other people are having to deal with it too, and that it doesn't seem like an easy fix for users.  If that's not the case and if anyone else has any suggestions, I'd sure appreciate any help.

At least it's pretty easy to "guess" where the buttons are most of the time.

---

### Post by Prosthetic Head on 2008-04-27
Hi,
I'm the one who posted it back in Feb. I guess it didn't get any attention as it was unconfirmed and I was the only one who had experienced / reported it. So thanks for taking the time to confirm it :)

---

### Post by Prosthetic Head on 2008-04-27
Hi again,
Just had a quick look and your sony is listed as using the "NeoMagic MagicMedia™ 256XL+" graphics chip.
My IBM 600E uses the "NeoMagic MagicMedia™ 256AV" 
So maybe it is an issue with the driver for this series of NeoMagic chips, and / or how whatever toolkit draws the widgits for the xfce4-terminal talks to it?

I could very well be wrong as i'm no expert on this type of issue, just a thought.

---

### Post by tyronenguyen on 2008-04-27
Ahoy,

I just wanted to say I also have this annoying issue of completely black title bar on the default terminal.  I also have other graphical glitches, like the screen not refreshing completely (when background windows are brought to the forefront, the previous forefront window is not completely erased).

I'm running Hardy Heron 8.04 (Installed fresh last Thursday) xubuntu on a Thinkpad 600e.

My lspci shows the Neomagic 256AV.  

How do I figure out if my video settings are correct?  if my video drivers are installed correctly?

```

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:02.0 CardBus bridge: Texas Instruments PCI1251A
00:02.1 CardBus bridge: Texas Instruments PCI1251A
00:06.0 Multimedia audio controller: Cirrus Logic CS 4610/11 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
01:00.0 VGA compatible controller: Neomagic Corporation NM2200 [MagicGraph 256AV] (rev 20)

```

Regards,
Tyrone

---

### Post by Prosthetic Head on 2008-04-28
My lspci comes up the same as yours, the only glitch I have experianced is the one I've already mentioned with xfce4-terminal. I run the desplay at 16bit colour depth instead of the default 24bit as otherwise it is VERY solw, but it is very usable at 16bit and I can't see any diffrence.

```

00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:02.0 CardBus bridge: Texas Instruments PCI1251A
00:02.1 CardBus bridge: Texas Instruments PCI1251A
00:06.0 Multimedia audio controller: Cirrus Logic CS 4610/11 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
01:00.0 VGA compatible controller: Neomagic Corporation NM2200 [MagicGraph 256AV] (rev 20)

```

_off topic_, but it took me ages to get sound to work on my 600e, if you have the same issue let me know and i'll link you to the fix :)

---

### Post by tyronenguyen on 2008-04-28
> **Prosthetic Head said:**
> My lspci comes up the same as yours, the only glitch I have experianced is the one I've already mentioned with xfce4-terminal. I run the desplay at 16bit colour depth instead of the default 24bit as otherwise it is VERY solw, but it is very usable at 16bit and I can't see any diffrence.


_off topic_, but it took me ages to get sound to work on my 600e, if you have the same issue let me know and i'll link you to the fix :)

I guess I'll assume mine is at 16-bit color since I am using it w/o much slowdown.  Although, my youtube videos are really choppy like slideshows. 

After I added some line to some file, the all black terminal borders are replaced with color streaks.  The colors are picked up from whatever window is underneath and the streaking happens when I drag the terminal window around.  

Oh yes, I would be most thankful if you could provide the link to the audio fix.

---

### Post by Taxi on 2008-04-28
Here's my lspci, for a *little bit* of diversity.  It's showing a Neomagic Corporation NM2160 [MagicGraph 128XD].

```
00:00.0 Host bridge: Intel Corporation 430TX - 82439TX MTXC (rev 01)
00:01.0 ISA bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 01)
00:01.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:01.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:01.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 01)
00:08.0 VGA compatible controller: Neomagic Corporation NM2160 [MagicGraph 128XD] (rev 01)
00:0a.0 CardBus bridge: Texas Instruments PCI1131 (rev 01)
00:0a.1 CardBus bridge: Texas Instruments PCI1131 (rev 01)
```

---

### Post by Prosthetic Head on 2008-04-29
Another case found, a friend of mine with an old sony laptop with the same graphics chip also has the same issue, so i think that is a highly likly culprit. 
We need somone who knows about graphics drivers and / or the rendering of those window decorations to take a look at the issue...

tyronenguyen: I've PMed you the audio fix :)

---

### Post by james_vanb on 2008-04-29
Upgraded to Hardy yesterday - Same problem on an old Dell Latitude CP M233ST - Has NeoMagic 2160 - Terminal is almost unusable.

Prosthetic Head - Assuming your IBM has the infamous cs4237b sound driver - I have the same on my Dell - Have you posted your solution in a Thread?  I would be interested in seeing if the solution I used is the same as yours.

---

### Post by Prosthetic Head on 2008-04-29
> **james_vanb said:**
> Upgraded to Hardy yesterday - Same problem on an old Dell Latitude CP M233ST - Has NeoMagic 2160 - Terminal is almost unusable.

Prosthetic Head - Assuming your IBM has the infamous cs4237b sound driver - I have the same on my Dell - Have you posted your solution in a Thread?  I would be interested in seeing if the solution I used is the same as yours.

I haven't posted it anywhere else, but seeing as 2 ppl have asked I've attached a guide i did for a friend with a 600e, hopefully it will help someone :)

---

### Post by tyronenguyen on 2008-04-30
Awesome, I finally got audio working.  Thank you!

One tip I have is that the initialize and disable quick boot is really important.  I turned off the laptop (not restart).  Went into bios, hit initialize, then disabled quick boot.  After exiting bios, xubuntu loaded up and 'aplay -l' showed my sound card.  Awesome!

---

### Post by james_vanb on 2008-04-30
The following is a link to the Bug Report filed by Prosthetic Head:

[https://bugs.launchpad.net/ubuntu/+source/xfce4-terminal/+bug/194769](https://bugs.launchpad.net/ubuntu/+source/xfce4-terminal/+bug/194769)

If you have this problem, I would encourage you to add a comment to the Bug Report as the priority for a fix has not been determined yet.

---

