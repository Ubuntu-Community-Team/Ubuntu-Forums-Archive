---
title: "Good NES emulator?"
date: 2010-05-19
forum: Gaming &amp; Leisure
---

### Post by HHx66 on 2010-05-19
I'm looking for a good NES emulator that runs good with a user interface that'll support 64 bit Karmic. Any ideas? I don't really like GFCEU

---

### Post by disturbedite on 2010-05-20
i don't know why everyone doesn't just use nestopia... :P
its the most accurate NES emulator.

---

### Post by hikaricore on 2010-05-20
> **disturbedite said:**
> i don't know why everyone doesn't just use nestopia... :P
its the most accurate NES emulator.

this is why they say opinions are like ********

---

### Post by disturbedite on 2010-05-21
> **hikaricore said:**
> this is why they say opinions are like ********

yeah, except its the majority opinion.

---

### Post by MC_Sketch on 2010-05-24
i use Jnes. yeah, it's a .exe, but i just run it through Wine and it runs perfectly.

---

### Post by tuxtorch on 2010-05-25
sudo apt-get install gfceu

:guitar:

---

### Post by CharmyBee on 2010-05-28
> **HHx66 said:**
> I don't really like GFCEU

Agreed, Nestopia is seconded. I don't think there's a viable substitute for its accuracy in this day and age, everything else seems only maintained for the sake of being maintained.

---

### Post by DoktorSeven on 2010-05-28
Nestopia is a pain to configure and set up correctly in my experience.  It also failed to find most of my ROMs, I think because the extension was an uppercase version of the standard NES ROM extension, and you can't select "all files".  It needs the NDS ROM in ~/.nestopia instead of, you know, just pointing at the file (and you have to manually copy in a couple of config files, rather than doing it itself).  Controller config was slow and tedious, having to separately configure each direction and button.

It's a nice enough emulator technically, but it's really a pain to actually *use*, and with NES emulators that emulate everything well enough and are easy to set up and configure, Nestopia seems like quite a clunky dinosaur by comparison.

---

### Post by mr.farenheit on 2010-05-29
i always used gfceu for the simple interface and it also seems to run the original famicom roms better.

---

### Post by zer010 on 2010-06-23
i would LOVE to use Nestopia, but I just can't seem to get the darn thing to make....it's really starting to frustrate me](*,)

---

### Post by Mike'sHardLinux on 2010-06-23
I couldn't get it to make, either. But, there is a workaround: Grab the Fedora .rpms and convert them to .deb with alien. It worked for me.

---

### Post by rahilm on 2010-06-23
i used alien to convert nestopia.. it is running, but i can't figure out the controls..

EDIT: got them in .nestopia folder. working fine.
I can't see how it is different form gfceu.. maybe i am using the wrong version. The windows version looked better. ALso had many features.

UPDATE:
Compiled it at last!! The compiled version is much much much better than the above version. Also has a cheat menu and can configure controls. Still less than the windows version though, which runs fine in wine.

---

### Post by Mike'sHardLinux on 2010-06-24
You must have grabbed some old .rpms. I have 1.40h-3 and it has all that stuff you said....cheat menu, configure controls.....

Anyway, how did you get it to compile?

---

### Post by hikaricore on 2010-06-24
I think you all underestimate the power of the launchpad ppas.

[https://launchpad.net/~nikil.mehta/+archive/emulators](https://launchpad.net/~nikil.mehta/+archive/emulators)

---

### Post by rahilm on 2010-06-25
> **Mike'sHardLinux said:**
> You must have grabbed some old .rpms. I have 1.40h-3 and it has all that stuff you said....cheat menu, configure controls.....

Anyway, how did you get it to compile?
Downloaded both the packages and extract.. put all contents of nst140_lnx_release_h inside the Nestopia140src.
install libsdl1.2-dev
```
sudo apt-get install libsdl1.2-dev
```then the regular make...

Now that you mention.. i checked it was v1.37.. got the new one with compiling though.

---

