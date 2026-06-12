---
title: "Doom 1"
date: 2012-03-23
forum: Gaming &amp; Leisure
---

### Post by Carnivorum on 2012-03-23
How can I play Doom 1 in Ubuntu?

---

### Post by Rodney9 on 2012-03-23
Available in the Software Centre

Chocolate doom is a modern, cross-platform doom engine with the major design goal of emulating the behaviour of vanilla Doom as close as is possible. For example, chocolate doom can read and write vanilla doom save games.

Unlike most modern doom engines, chocolate doom is not derived from the Boom source-port and does not inherit its features (or bugs).

Chocolate doom requires a doom-wad to play. If you have a copy of the commercial games Doom or Doom 2, you can generate a doom-wad package using "game-data-packager".


Rodney

---

### Post by mastablasta on 2012-03-23
you can use DosBOX to get original way including the low resolution :-)
 
or use one of the projects such as zdoom or similar which will launch it at high resolution or maybe even with openGL using HDR lighting, 3D monsters and such. 
[http://en.wikipedia.org/wiki/Jdoom](http://en.wikipedia.org/wiki/Jdoom)
 
Skulltag is preety good.

---

### Post by Carnivorum on 2012-03-23
Thanks

---

### Post by gdbutcher on 2012-03-23
I'd also recomend Skulltag:  [http://www.skulltag.net]("http://www.skulltag.net")

---

### Post by Cavsfan on 2012-03-23
Never mind

---

### Post by Cavsfan on 2012-03-23
Never mind

---

### Post by kazztan0325 on 2012-03-23
You can download Doom wad files here:
[http://www.pc-freak.net/blog/doom-1-doom-2-doom-3-game-wad-files-for-download-playing-doom-on-debian-linux-via-freedoom-open-source-doom-engine/]("http://www.pc-freak.net/blog/doom-1-doom-2-doom-3-game-wad-files-for-download-playing-doom-on-debian-linux-via-freedoom-open-source-doom-engine/")

And you would be able to refer following site for Doom Wad.
"Doom Wad Station"
[http://doomwadstation.com/]("http://doomwadstation.com/")

---

### Post by Cavsfan on 2012-03-23
> **kazztan0325 said:**
> You can download Doom wad files here:
[http://www.pc-freak.net/blog/doom-1-doom-2-doom-3-game-wad-files-for-download-playing-doom-on-debian-linux-via-freedoom-open-source-doom-engine/](http://www.pc-freak.net/blog/doom-1-doom-2-doom-3-game-wad-files-for-download-playing-doom-on-debian-linux-via-freedoom-open-source-doom-engine/)

And you would be able to refer following site for Doom Wad.
"Doom Wad Station"
[http://doomwadstation.com/](http://doomwadstation.com/)


Thanks

---

### Post by kazztan0325 on 2012-03-23
You are welcome, Cavsfan!

And in this connection, you can install following FPS games with Software Center or Synaptic Package Manager, if you are interested in. (In case you did not know.)

- nexuiz
- sauerbraten
- alien-arena
- assaultcube
- warsow

---

### Post by oldos2er on 2012-03-23
Thread moved to Gaming & Leisure.

---

### Post by Cavsfan on 2012-03-23
I have a WAD file but, still cannot get past this error. It starts and runs for about 5 seconds and then quits:

```
cavsfan@cavsfan-desktop:~$ chocolate-doom
                         Chocolate Doom 1.2.1
Z_Init: Init zone memory allocation daemon. 
zone memory: 0x7f24d3b94010, 1000000 allocated for zone
DEH_Init: Init Dehacked support.
V_Init: allocate screens.
M_LoadDefaults: Load system defaults.
saving config in /home/cavsfan/.chocolate-doom/default.cfg
W_Init: Init WADfiles.
 adding /usr/share/games/doom/doom1.wad
===========================================================================
                            DOOM Shareware
===========================================================================
 Chocolate Doom is free software, covered by the GNU General Public
 License.  There is NO warranty; not even for MERCHANTABILITY or FITNESS
 FOR A PARTICULAR PURPOSE. You are welcome to change and distribute
 copies under certain conditions. See the source for more information.
===========================================================================
M_Init: Init miscellaneous info.
R_Init: Init DOOM refresh daemon - [...................]
P_Init: Init Playloop state.
I_Init: Setting up machine state.
NET_Init: Initialise network subsystem.
S_Init: Setting up sound.
D_CheckNetGame: Checking network game status.
startskill 2  deathmatch: 0  startmap: 1  startepisode: 1
player 1 of 1 (1 nodes)
Emulating the behavior of the 'Doom 1.9' executable.
HU_Init: Setting up heads up display.
ST_Init: Init status bar.

Error: Demo is from a different game version!
(read 108, should be 109)

*** You may need to upgrade your version of Doom to v1.9. ***
    See: http://doomworld.com/files/patches.shtml
    This appears to be v1.8.
cavsfan@cavsfan-desktop:~$ 
```
prdoom will run with this command **prboom -file /usr/share/games/doom/prboom.wad**
But, it is just a little box and will not go fullscreen.
Thanks!

---

### Post by kazztan0325 on 2012-03-23
I have played both chocolate-doom and prboom on my Notebook PC (original screen resolution is 1440x900), it seems game screen of them are 1200x900, because original screen aspect ratio of these games are 4:3).

Sorry, I also don't know why in your case it is just a little box, and also don't know why in your case chocolate-doom won't run.

What about opening and checking your files 'chocolate-doom.cfg' which is in '.chocolate-doom' folder and 'prboom.cfg' which is in '.prboom' folder with Text editor?

---

### Post by Cavsfan on 2012-03-23
> **kazztan0325 said:**
> I have played both chocolate-doom and prboom on my Notebook PC (original screen resolution is 1440x900), it seems game screen of them are 1200x900, because original screen aspect ratio of these games are 4:3).

Sorry, I also don't know why in your case it is just a little box, and also don't know why in your case chocolate-doom won't run.

What about opening and checking your files 'chocolate-doom.cfg' which is in '.chocolate-doom' folder and 'prboom.cfg' which is in '.prboom' folder with Text editor?

Thanks! There is no files in '.chocolate-doom' but, I was able to fix prboom. I changed fullscreeen 0 to 1 and that fixed it.

Looks like there is a bug about needing to upgrade from v1.8 to v1.9 for chocolate doom. 
I could not fix it although there were workarounds in the bug report.

---

### Post by kazztan0325 on 2012-03-23
> **Cavsfan said:**
> Thanks! There is no files in '.chocolate-doom' but, I was able to fix prboom. I changed fullscreeen 0 to 1 and that fixed it.
You are welcome!
I'm glad to hear you fixed prboom.

> **Cavsfan said:**
> Looks like there is a bug about needing to upgrade from v1.8 to v1.9 for chocolate doom. 
I could not fix it although there were workarounds in the bug report.
I don't understand why you cannot run chocolate doom though I can play it without any workarounds.
I intend to research on it when I have time.

---

### Post by Cavsfan on 2012-03-26
Thanks! In my searches for a fix, all I encountered was bug reports where people were getting the same error as I was:

*** You may need to upgrade your version of Doom to v1.9. *** 
    See: [http://doomworld.com/files/patches.shtml](http://doomworld.com/files/patches.shtml)     
This appears to be v1.8.

In the link above I could not find anything to fix it. It redirected to another page.

---

### Post by fragglet on 2012-03-26
Hi,

I'm the author of Chocolate Doom. I see you're having some problems so I thought I'd chime in and provide some help.

The error message you've quoted describes your problem. You're using v1.8 of the shareware IWAD file (doom1.wad). Chocolate Doom only supports v1.9 - you need to upgrade. As it's the shareware version you can just download it.

It looks like you're using the shareware IWAD from Ubuntu's doom-wad-shareware package. This is actually an old version - because of a [bug]("https://bugs.launchpad.net/ubuntu/+source/doom-wad-shareware/+bug/608806"), the package mistakenly contains the v1.8 file and not the v1.9 file. This was fixed a couple of years ago in Debian but Ubuntu still seems to include the old package. The easiest solution is to download the [Debian package]("http://packages.debian.org/squeeze/doom-wad-shareware") and install that manually (with dpkg -i).

Alternatively you can download [the Windows port of Doom]("ftp://ftp.fu-berlin.de/pc/msdos/games/idgames/idstuff/doom/win95/doom95.zip"), extract doom1.wad and use that directly (chocolate-doom -iwad doom1.wad).

Finally, if this is all too much, this problem only occurs when it tries to play back a demo. At the title screen, if you make sure to quickly start a new game before the first demo plays, the game should run fine without any problems.

---

### Post by perspectoff on 2012-03-26
Oh, but please install Skulltag and play Skulltag instead. I'd love to have an online competitor!

Skulltag is a modified ZDoom, but it automates wad installation for you. Doom on steroids.

You do need the Freedoom IWAD if you don't have the Doom2 wad.

Installation instructions for Skulltag, PRBoom (which is kind of a waste of time, IMO), and ZDoom are at

[http://ubuntuguide.org/wiki/Ubuntu_Oneiric_Games_and_Entertainment#Doom](http://ubuntuguide.org/wiki/Ubuntu_Oneiric_Games_and_Entertainment#Doom)

---

### Post by Cavsfan on 2012-03-26
> **fragglet said:**
> Hi,

I'm the author of Chocolate Doom. I see you're having some problems so I thought I'd chime in and provide some help.

The error message you've quoted describes your problem. You're using v1.8 of the shareware IWAD file (doom1.wad). Chocolate Doom only supports v1.9 - you need to upgrade. As it's the shareware version you can just download it.

It looks like you're using the shareware IWAD from Ubuntu's doom-wad-shareware package. This is actually an old version - because of a [bug]("https://bugs.launchpad.net/ubuntu/+source/doom-wad-shareware/+bug/608806"), the package mistakenly contains the v1.8 file and not the v1.9 file. This was fixed a couple of years ago in Debian but Ubuntu still seems to include the old package. The easiest solution is to download the [Debian package]("http://packages.debian.org/squeeze/doom-wad-shareware") and install that manually (with dpkg -i).

Alternatively you can download [the Windows port of Doom]("ftp://ftp.fu-berlin.de/pc/msdos/games/idgames/idstuff/doom/win95/doom95.zip"), extract doom1.wad and use that directly (chocolate-doom -iwad doom1.wad).

Finally, if this is all too much, this problem only occurs when it tries to play back a demo. At the title screen, if you make sure to quickly start a new game before the first demo plays, the game should run fine without any problems.

Thanks **fragglet**!
I was able to use the 1st method you mentioned. But, when I ran it, it was called Free Doom.
The monsters didn't look like the ones in Doom.
Is that the way it is supposed to be? The menu item even says "Free Doom".
I think there is something I am not doing right maybe?

---

### Post by Cavsfan on 2012-03-26
Sorry for the confusion when I entered chocolate-doom everything worked great!!!
Thanks! I'll fix the menu item to point to the right program.

---

### Post by Cavsfan on 2012-03-26
Oh, forgot to ask is there an open gl option or is **chocolate-doom** the only command I can use.
Thanks again!

Found out how to run the game with a WAD from the full game my son had purchased:
**chocolate-doom -iwad DOOM.WAD**

But, still wondering about the opengl option
Thanks

---

### Post by kazztan0325 on 2012-03-29
> **Cavsfan said:**
> But, still wondering about the opengl option
Thanks
It seems chocolate-doom doesn't have OpenGL option, though prboom has it.
Or it would be possible I just don't know if chocolate-doom has OpenGL option which is set by command in Terminal...

---

### Post by fragglet on 2012-03-29
> **kazztan0325 said:**
> It seems chocolate-doom doesn't have OpenGL option, though prboom has it.
Or it would be possible I just don't know if chocolate-doom has OpenGL option which is set by command in Terminal...
OpenGL wouldn't really fit with the philosophy of the project. If you want features like that you're better off using a different port - PrBoom+ would be one option, or you could try a port like JDoom (Doomsday Engine).

---

### Post by kazztan0325 on 2012-03-29
> **fragglet said:**
> OpenGL wouldn't really fit with the philosophy of the project. If you want features like that you're better off using a different port - PrBoom+ would be one option, or you could try a port like JDoom (Doomsday Engine).

Hi fragglet,

Thank you for your reply and suggestion.
I understood your project's situation.
I hope your project would go on wheels.

Cheers!
kazz

---

