---
title: "ixbar3000 frontend"
date: 2014-04-19
forum: Emulators
---

### Post by ix-jpn on 2014-04-19
Hello!

I'm the developer of the ixbar3000 frontend. ixbar3000 supports a lot of systems (everything I know) and it's quite ready for general usage. I develop in on Ubuntu, but it's platform-agnostic so it also runs on windows. I'm a engineer not a marketeer so while it's awesome it's not known :P

The purpose of the program is to simplify emulator usage although with ixbar3000 you can also run native software. ixbar3000 is open source, made with tcl/tk. I tried to make the best frontend and imho I've already achieved that goal. 

Here's a video of imported Gamebase Amiga: [http://youtu.be/XzPGq4Srd8w](http://youtu.be/XzPGq4Srd8w)

[Twitter]("https://twitter.com/DeusIX_imxn")
[Homepage]("http://imxn.net/wordpress/?page_id=14")
[Download]("http://sourceforge.net/projects/ixbar3000/")

---

### Post by adec2 on 2014-04-19
Many thanks, I will give this a try!

---

### Post by ix-jpn on 2014-05-08
Anyone up to testing multiplayer? It will take some time and patience, but AFAIK, it's possible!

---

### Post by General_Faliure on 2014-05-09
Looks good.
I'll try it on a test system.
For my cab i will stick with Mahcade.
Will you support Daphne (laserdisc)?

---

### Post by ix-jpn on 2014-05-09
Yeah, ixbar3000 isn't really designed for cabinets. It kind of requires keyboard+mouse to use. [COLOR=#ffffff][SIZE=1]for now...[/SIZE][/COLOR]

In order to get Daphne working with ixbar3000.
1. I need a list of entries (games) in a datfile or similar. This is required to populate the romlist.
2. Emulator needs to be usable with terminal/CLI. Looking at the daphne documentation this is OK.
3. Then I'd may need to add a new system (platform) to ixbar3000. If it needs one... This is a thing I'm unfamiliar with.

Is Daphne Emulator or a Platform? Is it like a MAME for laserdisks? Is MAME's competitor or what? Can't MAME do laserz!?
tr;dr. It is possible as there are no technical issues. I just have to figure out what it is: You seem to know, enlighten me. ;)

---

### Post by General_Faliure on 2014-05-10
Daphne is an emulator, like Mame.
Mame has preliminary support for a few laserdisc games, but Daphne supports them all.
It only seems like the development has been stopped.
It took a bit of effort to get it running on lubuntu 14.04 (64 bit), but i have got it working now.
Daphne has it's own frontend, but can be run from cli, as i do from within Mahcade.

---

### Post by ix-jpn on 2014-05-21
I made two new videos
1. [Gamebase64]("http://youtu.be/AZmTESleLZg")
2. [Search Functionality]("http://youtu.be/vS9C5BpeWOI")


And Daphne progress :P
[ATTACH=CONFIG]253351[/ATTACH]
I do not know how to load them though...

---

### Post by General_Faliure on 2014-05-26
Here is my Daphne start script for Mahcade (wahcade)
With this script i can start all the games from within Mahcade;

[name] vldp -framefile ~/emulators/Laserdisk/[name]/[name].txt -fullscreen -blank_searches -min_seek_delay 1000 -seek_frames_per_ms 20 -homedir ~/emulators/Laserdisk/daphne -fastboot -sound_buffer 2048 -x 1280 -y 1024

For example Space Ace; i use the enhanced rom: sae.zip.
The framefile is renamed to sae.txt
The video directory is also renamed to sae.

This works for Mahcade, which is based on Python.
Hope it helps you

---

### Post by ix-jpn on 2014-06-07
I released v024.
 No Daphne yet, but the new version does have multiplayer support with mednafen.

---

