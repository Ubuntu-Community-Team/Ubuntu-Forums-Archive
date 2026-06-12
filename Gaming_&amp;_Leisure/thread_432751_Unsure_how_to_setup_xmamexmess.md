---
title: "Unsure how to setup xmame/xmess"
date: 2007-05-04
forum: Gaming &amp; Leisure
---

### Post by whein on 2007-05-04
I downloaded and installed all the deb packages easily enough through Synaptic.  Unfortunately I'm having trouble finding a clear explanation of how to setup the directories for xmess and how to launch the program with the correct options to play any given ROM.  I read through the Mess FAQ on cvs.mess.org but the only somewhat helpful section was> Okay, I got some BIOSes and images, now where do I put them?

BIOSes should go, still zipped, in the BIOS subfolder of wherever you put MESS. Game images should go into the SOFTWARE\[system name] folder. They can still be zipped, but only one image per zip file.

How do I start the MESS application?

For DOS, type "mess [system] [device] [game] [options]", where [system] is the system driver name, [device] is the type of ROM, [game] is the filename of the ROM, and options are command line options. Valid [device] names (eg -cart and -flop) can be found by using "mess -listdevices" and valid options are listed in the mess.txt and msdos.txt files.

For example:

mess nes -cart zelda.nes -nosound (This will run the Zelda game on the Nintendo system without sound. See mess.txt for more examples.

For UNIX/Linux, do the same thing except the name of the program is xmess.
Couple problems:
 - I cannot find a copy of mess.txt ANYWHERE (Google wasn't much help either).
 - typing xmess in a terminal does nothing.  I *think* it's supposed to be xmess.x11 on Ubuntu, but correct me if I'm wrong.
 - I don't understand what the "SOFTWARE\[system name] folder" means.  Should I make a directory $SOFT/nes/ and put zelda.zip in it, where $SOFT is the software path as defined by xmessrc?  Is "SOFTWARE" some other directory?
 - How exactly do I get a BIOS for an original Nintendo system???  Should I manage to aquire one, what directory do I then put it into?

Can anyone tell me what to put where and how to launch the program from the terminal?  My end goal is to get xmess running through my Myth front end (which already works).  I'm running an up to date Fiesty installation.  Any help is appreciated.
-Will

---

### Post by DoktorSeven on 2007-05-04
NES doesn't need BIOS; just do

xmess nes -cart /path/to/rom.zip

Course, there are a ton of other options, and I don't know of a frontend for Linux xmess, so you'll just have to type **xmess** to get a huge list of what options to use to make it play right.

Easier way to play NES games: get fceu and gfceu, run gfceu.

---

