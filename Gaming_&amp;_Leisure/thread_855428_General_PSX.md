---
title: "General PSX"
date: 2008-07-10
forum: Gaming &amp; Leisure
---

### Post by lordhaworth on 2008-07-10
Hey all
I'm new to ps emulation, i've downloaded PSX through the Add/Remove Programs (im running hardy) and that all installed fine. Can anyone help me with how to actually start playing games? Ive tried just putting in a disk (resident evil 2, and then 3- great games!) but not really sure how to get them running!
Any help would be appreciated, the ability to play my playstation games on this computer would be great!

Cheers

Tom

---

### Post by BossGreen on 2008-07-10
I dont use emulators myself, but my friend does it alot.  i think the way he does it, is he downloads the emulator, then he goes to a site and downloads the game from there.  i think it might be illegal/pirating... but yea.  thats how he plays games.
but then again it might not be the same because he only uses nintendo/gba/snes emulators.  but i'd imagine it follows the same kinda guidelines.

---

### Post by lordhaworth on 2008-07-10
Yeah Ive tried it with gameboy and that generally is pirated, but i thought PSX was something you download to allow you to play games you already own (not just should already own) straight from the disk

---

### Post by hessiess on 2008-07-10
with pSX just go file->insert CD drive.

---

### Post by acoustibop on 2008-07-10
Since he installed through "Add/Remove Programs" (Synaptic?) I don't think it can be pSX emulator lordhaworth is talking about.  Probably PCSX.

Tom, try [pSX Emulator]("http://psxemulator.gazaxian.com/") instead.  It's pluginless, so it's a lot less hassle than plugin-based Playstation emulators, and it works a lot better.

You can't install it through Synaptic, as it's not in the repositories, but it's still very easy; just download the package to a suitable location (I'd suggest your Home folder) and decompress it (it'll decompress to a folder called pSX).  You'll need to install libgtkglext1 (in the repositories; either do```
sudo apt-get install libgtkglext1
``` or install it through Synaptic) and you'll need a Playstation BIOS - don't ask here, as it's illegal to download them, but they're not hard to find - which you put in your ~/pSX/bios folder.

Then you can run it straight away, without configuration, although if you have a controller, obviously you'll need to configure that.

However, if you're running a 64bit bit system, installing the required libraries is a little more complicated - you neglected to say much about your system.

Yes, playing games that you own, or ripping your own games to backup copies that you can play is perfectly legal.  It is *not* legal to download Playstation games.

---

### Post by lordhaworth on 2008-07-12
Yeah sorry for the time out away from this
I did realise that it was PCSX, and after reading around more have seen thats its not exactly the most highly favoured.
Thanks for your advice ill try this other emulator

---

### Post by disturbedite on 2008-07-12
just my 2 cents, but i too highly recommend pSX over any other playstation emulator.

---

