---
title: "Is there a normal driving game for(or emulated on) linux?"
date: 2008-05-24
forum: Gaming &amp; Leisure
---

### Post by emshains on 2008-05-24
I've searched all over the wine app-db and havent found any normal game, that would run smooth or even work propely. There are no really functional natvie driving games, and I have looked all over the place. The best I've found is vDrift, but it was as bugy as **HELL**. 

If you know any good native or emulated game that is interesting and isnt buggy as **HELL**, please post a link.

---

### Post by atomkarinca on 2008-05-24
Have you tried [TORCS]("http://torcs.sourceforge.net/")? It's in the repos:

```
sudo apt-get install torcs
```

---

### Post by Perfect Storm on 2008-05-24
What about [Racer](http://gaming.gwos.org/doku.php/games:alphabetical:r:racer)?

---

### Post by emshains on 2008-05-24
> **atomkarinca said:**
> Have you tried [TORCS]("http://torcs.sourceforge.net/")? It's in the repos:

```
sudo apt-get install torcs
```

Torcs is actually really bad. The sound is unbearable and the graphics are discusting. It would be a great game 10 years ago.

---

### Post by emshains on 2008-05-24
> **Artificial Intelligence said:**
> What about [Racer](http://gaming.gwos.org/doku.php/games:alphabetical:r:racer)?

When I tried to put new cars into racer's directory it either messed up and the game didnt launch, or it just acted like nothing had happened and there were no new cars in the menu.

---

### Post by acoustibop on 2008-05-24
As far as emulation is concerned, emshains, there are emulators for most consoles up to about Playstation 2 level - although that one, [PCSX2]("http://www.pcsx2.net/"), needs a pretty high end machine and might not deliver good enough fps for driving games.

I don't find myself playing driving games, so I don't know what games there are for what consoles, but I can point you to a few good emulators.

For both the Sega Master System and Nintendo Entertainment System, I find myself using Mednafen - one of the members here, franmichaels, has posted a [.deb for version 0.8.8-1]("http://ubuntuforums.org/showpost.php?p=4655351&postcount=26"), which is needed for good SMS emulation.  I suspect these platforms may not support the sort of driving games you're looking for, though.

Going up from there, we have GENS for Sega Genesis, including 32X and CD versions - megamaced has posted [a .deb for what's probably the best version available]("http://ubuntuforums.org/showpost.php?p=4997623&postcount=329").

There's ZSNES for the Super Nintendo - the current version is in the Hardy and Gutsy repositories.

Then there's [pSX Emulator]("http://psxemulator.gazaxian.com/") for the Sony Playstation.  You just decompress the download package wherever you want - your Home folder is favourite - and run the executable.  However, you'll need to install libgtkglext1 and possibly the -dev package as well (in the repositories) and you'll need the BIOS from a Playstation.  Since, unlike the other Playstation emulators available for Linux, pSX is pluginless, configuration is simple and it runs much more evenly.

Lastly, for the Nintendo 64 console, there's [Mupen64Plus]("http://code.google.com/p/mupen64plus/").  There is a binary distribution, but you'll need to run the install.sh included in the package; since Mupen64Plus is a plugin-based emulator, you'll need to configure the plugins.  Runs nicely on quite mid-range machines.

---

### Post by Steve413z on 2008-05-24
torcs is cool

---

### Post by emshains on 2008-05-25
Well, ToRCS would be cool, if it had normal graphics, it wouldnt lag on 1.6 ghz, 768 mb ram and a 7300GT. And then we meet the sound, now thats a thing to laugh about.

---

### Post by galv on 2008-05-28
> **emshains said:**
> Well, ToRCS would be cool, if it had normal graphics, it wouldnt lag on 1.6 ghz, 768 mb ram and a 7300GT. And then we meet the sound, now thats a thing to laugh about.

I do ~60fps with a similar graphics cards, but my processor is dual-core.
BTW, I really like TORCS! :)

---

### Post by lvlo on 2008-05-30
[Live For Speed]("http://lfs.net") + Wine is my choise.

---

