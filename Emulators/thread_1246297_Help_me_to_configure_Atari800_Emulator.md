---
title: "Help me to configure Atari800 Emulator"
date: 2009-08-21
forum: Emulators
---

### Post by VirtualWaver on 2009-08-21
Hi all!

Recently I downloaded an Atari800 Emulator via console "apt-get install atari800". And I can't run it. When I run it via terminal "atari800", the emulator's screen came up and it says "Sorry, this program needs a really Atari/OS to run". I downloaded the original ROM files from **atari**800.**sourceforge**.net and configured paths in atari800.cfg, but still no luck. I have tried also do it via terminal "atari800 xlxe_rom ~/Desktop/ATARIXL.ROM but still the same error. Along with emulator's error, the terminal says "Error loading ROM image: atarixl.rom" but I configured all the paths correctly...  And, what is the worse, I found no instructions in the internet and no topics with solutions. 
I wonder if someone could help me to solve this annoying puzzle and run Atari800. 

Thank you in advance.

---

### Post by Newfoundlander on 2009-08-21
I'm a long-time Atari user but I have no experience with the 800, only the ST, 2600, and Jaguar.

If you get no responses here, you may wish to try these sites:

[http://www.atari.org/](http://www.atari.org/)

[http://www.atariage.com/](http://www.atariage.com/)

---

### Post by GoS_ on 2009-08-23
Try renaming the ROMs in lowercase. That would explain the "Error loading ROM image: atarixl.rom" when your command line argument was in uppercase.  I think that's the same problem I had a few months back.  Aside from that it sounds like you were doing everything right.  I hope you can get it to work.  The Atari 8 bits are really fun computers :)

---

### Post by Brebs on 2009-08-23
You can see for yourself where the program is looking for its ROM files:

```
cd ~
strace -e trace=file atari800 > atari800.txt 2>&1
grep -i rom atari800.txt
```

---

### Post by VirtualWaver on 2009-08-23
Thanks for your help guys! The problem was in .atari.cfg and in uppercase letters. It's Linux after all not Windows! ))) Now everything works fine. In conclusion, I would like to write a detailed manual for other people who experienced (or may experience) the same problem.

[CENTER][SIZE=2][B]HOW TO INSTALL AND CONFIGURE ATARI 800 
EMULATOR ON JAUNTY JACKALOPE:[/B][/SIZE]
[/CENTER]
 
**1.** First, we need to get atari800. We need to go to the terminal, type ```
 sudo apt-get install atari800 
``` and wait until atari800 will be installed.

**2.** Next, we need to download Atari original XL ROMs. They _**are not**_ game ROMs. Those ROMs needed for emulator to work. The ROMs are located here:

[http://sourceforge.net/projects/atari800/files/](http://sourceforge.net/projects/atari800/files/)

We need to follow the link and click to the **xf25.zip** and download it. Place it in your desktop, we will deal with it later. Along with xf25.zip, we need 2 more ROMs for Atari800. To get them, we need to follow this link:

[http://gnu.ethz.ch/atr/](http://gnu.ethz.ch/atr/)

and download **Atariosa.rom** and **atari5200.rom** files. After downloading them, we will have on our desktop those 2 files and xf25.zip archive.

**3.** Extract files from xf25.zip archive. After extracting leave **ATARIBAS.ROM**, **ATARIOSB.ROM** and **ATARIXL.ROM** and delete other files from that archive - we don't need them.

**4.** Now we have 5 files on our desktop -  ATARIBAS.ROM, ATARIOSB.ROM, ATARIXL.ROM, Atariosa.rom and atari5200.rom. 
First, we need to **rename** atari5200.rom to just **5200.rom**. 
Second, we need to **rename** all our files to **lowercase**, e.g. **ataribas.rom**, **atariosb.rom**, **atarixl.rom**, **atariosa.rom** and **5200.rom**. 
Now we have those 5 files with **lowercase** on our desktop.

**5.** Now we need to copy those 5 files into our home folder, e.g. /home/yourusername/.

**6****.** We almost finish. Now we need to have a launcher in our Application - Games folder, because originally Atari800 emulator doesn't has its launcher. We need to go to the System - Preferences - Main Menu than go to the Games section and press New Item button. In the type section leave Application, in the Name section type Atari 800XL, in the Command section type ```
 atari800 -width 800 -height 600 -dsprate 48000 -windowed 
``` (this will run Atari800 in a window with 800x600 resolution and with audio sample rate 48000Khz. If you want to run it in full screen mode, just skip -windowed argument) and in the Comment section type Atari 800XL Emulator. Then choose a picture for it, press Close button and quit Main Menu. Now we have this launcher in our Application - Games folder. Go to that folder and click on the Atari 800XL.

**7.** After executing Atari 800XL, the Self Test window will appear. We need to press F1 to quit it. Now we are in emulator's GUI. All we need is to press Run Atari Program, choose the game and play it! That's all! Enjoy the power of Atari 800XL!

To find game roms we need to google for it. A great example is [http://www.atarimania.com](http://www.atarimania.com), the section 400 800 XL XE - Games

Good luck and enjoy!

**PS:** As some links may do not contain the necessary files anymore, I've uploaded all the necessary files for the emulator as well as some atari classic games in one archive. Just download the archive and extract all the files and a folder called "Atari Roms" (this is atari games) into your home folder and follow the instructions. 

Here is links: 

[http://rapidshare.com/files/373205743/Atari_800_emulator_and_games_for_Ubuntu.rar.html](http://rapidshare.com/files/373205743/Atari_800_emulator_and_games_for_Ubuntu.rar.html)

or

[http://www.megaupload.com/?d=XU24RA3L](http://www.megaupload.com/?d=XU24RA3L)

Enjoy!

---

### Post by atari130xe on 2010-06-07
Hello VirtualWaver, thanks for the tutorial, but still can't load the Atari Roms (I just have copied the 5 roms into my home folder) start de emulators and does not load (sys roms) any help?
thanks!

---

### Post by atari130xe on 2010-06-07
> **atari130xe said:**
> Hello VirtualWaver, thanks for the tutorial, but still can't load the Atari Roms (I just have copied the 5 roms into my home folder) start de emulators and does not load (sys roms) any help?
thanks!

Sorry I have found the problem, the roms I have downloaded were in CAPS so now they work ok. Any way I cant remember the keayboard layout on the 130xe (my first Atari) so I dont remember how to load an .atr file, etc. could you give me that info pls? thanks once again!

---

### Post by Brebs on 2010-06-07
Just for future reference, you can see what files the program is looking for:

strace -e trace=file whateveryourexecutableis

---

### Post by afrodeity on 2010-11-20
none of the download links for Atariosa.rom and atari5200.rom work.

UPDATE: [http://aminet.net/package/misc/emu/atari800-mos](http://aminet.net/package/misc/emu/atari800-mos)

and [http://www.xl-project.com/](http://www.xl-project.com/)

---

### Post by ericitaquera on 2011-03-06
Instead of gathering flying files around your home dir, try the following:

Open atari800 (atari800 -windowed) and press F1. You'll be led to the configuration options. After set all files and dir, close it and reopen.

Regards.

---

### Post by honeybear on 2011-03-13
> **VirtualWaver said:**
> Thanks for your help guys! The problem was in .atari.cfg and in uppercase letters. It's Linux after all not Windows! ))) Now everything works fine. In conclusion, I would like to write a detailed manual for other people who experienced (or may experience) the same problem.

[CENTER][SIZE=2][B]HOW TO INSTALL AND CONFIGURE ATARI 800 
EMULATOR ON JAUNTY JACKALOPE:[/B][/SIZE]
[/CENTER]
 
**1.** First, we need to get atari800. We need to go to the terminal, type ```
 sudo apt-get install atari800 
``` and wait until atari800 will be installed.

**2.** Next, we need to download Atari original XL ROMs. They _**are not**_ game ROMs. Those ROMs needed for emulator to work. The ROMs are located here:

[http://sourceforge.net/projects/atari800/files/](http://sourceforge.net/projects/atari800/files/)

We need to follow the link and click to the **xf25.zip** and download it. Place it in your desktop, we will deal with it later. Along with xf25.zip, we need 2 more ROMs for Atari800. To get them, we need to follow this link:

[http://gnu.ethz.ch/atr/](http://gnu.ethz.ch/atr/)

and download **Atariosa.rom** and **atari5200.rom** files. After downloading them, we will have on our desktop those 2 files and xf25.zip archive.

**3.** Extract files from xf25.zip archive. After extracting leave **ATARIBAS.ROM**, **ATARIOSB.ROM** and **ATARIXL.ROM** and delete other files from that archive - we don't need them.

**4.** Now we have 5 files on our desktop -  ATARIBAS.ROM, ATARIOSB.ROM, ATARIXL.ROM, Atariosa.rom and atari5200.rom. 
First, we need to **rename** atari5200.rom to just **5200.rom**. 
Second, we need to **rename** all our files to **lowercase**, e.g. **ataribas.rom**, **atariosb.rom**, **atarixl.rom**, **atariosa.rom** and **5200.rom**. 
Now we have those 5 files with **lowercase** on our desktop.

**5.** Now we need to copy those 5 files into our home folder, e.g. /home/yourusername/.

**6****.** We almost finish. Now we need to have a launcher in our Application - Games folder, because originally Atari800 emulator doesn't has its launcher. We need to go to the System - Preferences - Main Menu than go to the Games section and press New Item button. In the type section leave Application, in the Name section type Atari 800XL, in the Command section type ```
 atari800 -width 800 -height 600 -dsprate 48000 -windowed 
``` (this will run Atari800 in a window with 800x600 resolution and with audio sample rate 48000Khz. If you want to run it in full screen mode, just skip -windowed argument) and in the Comment section type Atari 800XL Emulator. Then choose a picture for it, press Close button and quit Main Menu. Now we have this launcher in our Application - Games folder. Go to that folder and click on the Atari 800XL.

**7.** After executing Atari 800XL, the Self Test window will appear. We need to press F1 to quit it. Now we are in emulator's GUI. All we need is to press Run Atari Program, choose the game and play it! That's all! Enjoy the power of Atari 800XL!

To find game roms we need to google for it. A great example is [http://www.atarimania.com](http://www.atarimania.com), the section 400 800 XL XE - Games

Good luck and enjoy!

**PS:** As some links may do not contain the necessary files anymore, I've uploaded all the necessary files for the emulator as well as some atari classic games in one archive. Just download the archive and extract all the files and a folder called "Atari Roms" (this is atari games) into your home folder and follow the instructions. 

Here is links: 

[http://rapidshare.com/files/373205743/Atari_800_emulator_and_games_for_Ubuntu.rar.html](http://rapidshare.com/files/373205743/Atari_800_emulator_and_games_for_Ubuntu.rar.html)

or

[http://www.megaupload.com/?d=XU24RA3L](http://www.megaupload.com/?d=XU24RA3L)

Enjoy!


what is the compatibility between the :
- 130xe
- what is an xe/xl atari, into atari800 prog
- 800xl
- 5200 
- and 7800 atari?
thx

---

### Post by Brien_H on 2011-10-23
Thank you very much, VirtualWaver (if you're here to read it.) That is the first real piece of documentation I've found anywhere on the internet.

My own problem doesn't seem to involve the OSes - I got it to pick them up using the following command-line parameters:

```
atari800 -osa_rom ~/ATARIBAS.ROM -osb_rom ~/ATARIOSB.ROM -xlxe_rom ~/ATARIXL.ROM 
```After that the program stops giving the "real OS required" screen. However, the game file is more of a problem. The sourceforge blurb claims the program can support .atr files, but how does one actually get them to run?

---

### Post by Brebs on 2011-10-23
> **Brien_H said:**
> .atr files
Specify the .atr file at the end of the commandline, e.g.:
```
atari800 -fullscreen -bilinear-filter -artif 0 -vsync -fit-screen height -image-aspect none /home/myusername/games/atari800/roms/joust.atr
```

---

### Post by OnkyC on 2012-03-09
works a treat! 8) ah the good ol' days...
still have my 800XL+100's of disk games, trade if you have some too.

---

