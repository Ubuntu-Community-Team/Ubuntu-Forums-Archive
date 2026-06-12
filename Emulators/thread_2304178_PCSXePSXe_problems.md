---
title: "PCSX/ePSXe problems"
date: 2015-11-24
forum: Emulators
---

### Post by oldmacaroni on 2015-11-24
So I downloaded pcsx from the software centre and when I run it it appears to be missing the top drop down menu bar (with the File/Config/Emulator/ ect..) It won't let me configure anything and when I try to run any isos it either loads a black screen then quits, or gives me an error message. I also downloaded the linux version of ePSXe and extracted it, but when I tried to run it nothing happened, even after downloading all the correct plugins and putting them in the right place along with my bios. I've pretty much given up on epsxe at this point but is there any thing I can do about pcsx?   
thanks in advance

---

### Post by michael-piziak on 2015-11-25
Have you tried to go to your home folder, choose view hidden files, and trash/delete the PCSX preference folder (or file).  It rebuild one upon next launch.

Just an idea.  It helps me a lot to do this with lots of programs that start to act up - including browsers.

---

### Post by oldmacaroni on 2015-11-26
I tried this few times but it didn't seem to do anything :\ thinking maybe it's a problem with my game isos instead? Does pcxs have diffuculties playing japanese games/iso?

---

### Post by deadflowr on 2015-11-27
What version of Ubuntu? (It can help)

Also in PCSX Ctrl +P should open the Bios and Plugins window.

PCSX has a dummy bios plugin, and usually does not work well with many games.
(The behavior of a black screen when trying to run a game with that bios is common, or is for me at least)

As for how well a Japanese game will run, don't know, can't say.

Also note that there are games that just won't play (or i've been told)
regardless of where they are from, or which emulator you run.

---

### Post by oldmacaroni on 2015-11-29
> **deadflowr said:**
> What version of Ubuntu? (It can help)

Also in PCSX Ctrl +P should open the Bios and Plugins window.

PCSX has a dummy bios plugin, and usually does not work well with many games.
(The behavior of a black screen when trying to run a game with that bios is common, or is for me at least)

As for how well a Japanese game will run, don't know, can't say.

Also note that there are games that just won't play (or i've been told)
regardless of where they are from, or which emulator you run.

Thanks much, I just changed my graphics plugin and selected my bios and it completely fixed the problem! My regular and Japanese games play fine.

---

