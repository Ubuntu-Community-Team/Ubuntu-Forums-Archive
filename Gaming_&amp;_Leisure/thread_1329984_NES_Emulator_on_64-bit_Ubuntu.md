---
title: "NES Emulator on 64-bit Ubuntu"
date: 2009-11-17
forum: Gaming &amp; Leisure
---

### Post by snakeman21 on 2009-11-17
I've tried every Linux NES Emulator I can find, and none of them seem to work on my system.  The only thing I can think is that I'm running 64-bit.  Does anyone know of an NES emulator that works on 64 bit?

---

### Post by module0000 on 2009-11-18
I use ZSNES on 64-bit without any problems.

---

### Post by saidinesh5 on 2009-11-18
the last time i had this problem, long time ago though... it was due to some problem in compiz... 
so turn off the desktop effects and check it out. it may work.

also run the emulator from the terminal and post the error messsages here.. may be that might get you answers quicker :)

---

### Post by mthei on 2009-11-18
Have you tried [FCEUX](http://fceux.com)? The version that comes with Ubuntu is out of date, and the packages (FCEUltra and GFCEU) have been discontinued in favour of FCEUX. Try installing the .deb on the download page and see if it works if you haven't already.

Edit: I should also add that it's not just Ubuntu who is still using the older version. Even Debian's unstable branch and Fedora's RPMFusion repo have the older versions.

Edited again to fix the link.

---

### Post by snakeman21 on 2009-11-18
> **module0000 said:**
> I use ZSNES on 64-bit without any problems.

I can't even install zsnes.  In the add/remove programs utility (now called the "ubuntu software center") it says:  Not available for your hardware architecture.

---

### Post by snakeman21 on 2009-11-18
> **mthei said:**
> Have you tried [FCEUX](http://fceux.org)? The version that comes with Ubuntu is out of date, and the packages (FCEUltra and GFCEU) have been discontinued in favour of FCEUX. Try installing the .deb on the download page and see if it works if you haven't already.

Edit: I should also add that it's not just Ubuntu who is still using the older version. Even Debian's unstable branch and Fedora's RPMFusion repo have the older versions.

Your link does not work.

EDIT:  I found the download page with a google search.  I've already been there, and there is no 64-bit version.  I tried installing it anyways, but as I suspected, it would not install.

---

### Post by BoyOfDestiny on 2009-11-19
[http://mednafen.sourceforge.net/](http://mednafen.sourceforge.net/)

Mednafen, 64-bit works fine and is in the Ubuntu repositories.

---

### Post by disturbedite on 2009-11-19
Nestopia is the hands-down most accurate NES there is, i recommend it.

---

### Post by snakeman21 on 2009-11-19
> **BoyOfDestiny said:**
> [http://mednafen.sourceforge.net/](http://mednafen.sourceforge.net/)

Mednafen, 64-bit works fine and is in the Ubuntu repositories.

OK, mednafen seems to work, thank you... Only problem is... How do you change the controls?  I can't seem to figure that out.

---

### Post by BoyOfDestiny on 2009-11-19
Press F1 in mednafen.
It will list the common hotkeys.

For mapping the player 1 controller press 

alt + shift + 1

Then it will cycle through directions and buttons (just press the key or gamepad button you want for each)

It will remember the settings, so it's basically a one time thing.

Enjoy!

P.S. Full list of short cut keys
[http://mednafen.sourceforge.net/documentation/#using-keys](http://mednafen.sourceforge.net/documentation/#using-keys)

---

### Post by dfreer on 2009-11-20
Once again, ZSNES is a Super Nintendo emulator. NOT a Nintendo emulator, they are two different systems. *facepalm*

+1 for Nestopia being the best, whether you can get it running in linux tho...

I used to use GFCEU back in the day, but it really wasn't an ideal solution (it did run on my 64-bit machine IIRC). And it is possible to run the 32-bit binary of ZSNES on your 64-bit machine, if you want to get into SNES emulation.

---

### Post by mister_playboy on 2009-11-21
> **dfreer said:**
> +1 for Nestopia being the best, whether you can get it running in linux tho...

I have it on my system...

Download the the source from [[COLOR="Red"]here[/COLOR]](http://sourceforge.net/projects/nestopia/files/Nestopia/v1.40/Nestopia140src.zip/download) and extract the contents into a folder... I'll call it Nestopia.

Download the Linux overlay from [[COLOR="Red"]here[/COLOR]](http://rbelmont.mameworld.info/nst140_lnx_release_h.zip) and extract the contents into the same folder as the source.

Open the terminal, go to the location of the folder Nestopia and type:

```
make
```
for single CPU computers
```
make -j3
```
for dual-cores or
```
make -j5
```
for quad-cores.

Create a folder in your home directory called .nestopia and copy NstDatabase.xml and nstcontrols from the Nestopia folder to the new .nestopia folder.

Double click on the file nst in the Nestopia folder to run the emulator... I don't think there is any "install" functionality, so you'll have to create a launcher manually if you want to run it from Applications in your panel.

---

