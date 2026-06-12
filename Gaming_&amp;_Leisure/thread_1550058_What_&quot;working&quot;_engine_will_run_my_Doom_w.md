---
title: "What &quot;working&quot; engine will run my Doom wad in Lucid?"
date: 2010-08-10
forum: Gaming &amp; Leisure
---

### Post by QwUo173Hy on 2010-08-10
The reason I ask is because chocolate-doom crashes and I've just read on another thread that prboom does too. I also tried a wine version running in dosbox, but that was tricky to setup (inconvenient, not difficult).

Anything native and working out there?

Thanks,
Jarlath
PS: [http://www.omgubuntu.co.uk/2010/07/211-free-wine-compatible-games-in-one.html](http://www.omgubuntu.co.uk/2010/07/211-free-wine-compatible-games-in-one.html)

---

### Post by ELD on 2010-08-10
Not sure how well it works but try:
[http://www.happypenguin.org/show?Doom%20Legacy](http://www.happypenguin.org/show?Doom%20Legacy)

---

### Post by QwUo173Hy on 2010-08-10
Thanks ELD. I tried one of the versions and it doesn't work straight off the bat. Maybe I'll just install dosbox and run it that way.

---

### Post by AveryMaurice on 2010-08-10
I managed to get Chocolate Doom to work by specifying my IWAD in the command line:

```
chocolate-doom -iwad Documents/Doom/DOOM.WAD
```

Of course, you would replace the location with your IWAD. Using the shareware WAD crashes all the time with demo errors for me.

You could probably just add your PWAD parameter after that, considering the WAD is Vanilla compatible. ;)

EDIT: Adding the nosound parameter seems to work too, but that of course removes the sound.

---

### Post by fragglet on 2010-08-10
> **jarlath said:**
> The reason I ask is because chocolate-doom crashes and I've just read on another thread that prboom does too. Hi,

I'm the author of Chocolate Doom.  Sorry to hear that you're experiencing trouble.  Can you give me some of the details of this crash? (error messages etc)  I may be able to help resolve your problem.


> **AveryMaurice said:**
> I managed to get Chocolate Doom to work by specifying my IWAD in the command line:

```
chocolate-doom -iwad Documents/Doom/DOOM.WAD
```

Of course, you would replace the location with your IWAD. Using the shareware WAD crashes all the time with demo errors for me.
If you're having demo problems, it's probably because you're using an out of date IWAD file.  You can download [this zip file](ftp://ftp.chg.ru/pub/games/idgames/idstuff/doom/win95/doom95.zip) which has the v1.9 shareware IWAD.

---

### Post by proteusmoteus on 2010-08-10
[doomsday]("http://dengine.net/") doom engine supports [addons]("http://dengine.net/addons") for [newer models and textures]("http://www.youtube.com/watch?v=3fWXL7INKFM") (still need original wads). Perhaps because I run 64bit newer doomsday builds   always made corrupted save games which was fixed by forcing install of   this [deb]("http://sites.google.com/site/sdcofer/deng_1.8.6_i386.deb"). If they work for you the latest builds can be installed from the [project repository]("http://dengine.net/linux")

---

### Post by mastablasta on 2010-08-11
what's wrong with zDoom?
 
 
BTW anyone knwos if jDoom works in Linux? It's awesome!!!

---

### Post by proteusmoteus on 2010-08-11
afik jdoom = doomsday, so see my post above yours

---

### Post by QwUo173Hy on 2010-08-12
Avery Maurice, thanks. The wad actually loads but freezes a while in.

@proteusmoteus, Thank you. I might give doomsday a look. At the moment, the debian version of prboom is working well, as mentioned in the bug report for prboom on launchpad (see comment no.7 here for the link [https://bugs.launchpad.net/ubuntu/+source/prboom/+bug/375498](https://bugs.launchpad.net/ubuntu/+source/prboom/+bug/375498)

@mastablasta, cool - I can check out zDoom too. I didn't realize that some of the new engines had enhancements.
> **fragglet said:**
> Hi,

I'm the author of Chocolate Doom.  Sorry to hear that you're experiencing trouble.  Can you give me some of the details of this crash? (error messages etc)  I may be able to help resolve your problem.
Hi Fragglet, the game plays fine for me for a while, then the whole thing freezes up (music keeps playing but no response to controls). I can CTL Alt F to a terminal and kill the chocolate-doom process from there, which is reported by 'top' to be at 99 percent cpu.
```
 Chocolate Doom is free software, covered by the GNU General Public
 License.  There is NO warranty; not even for MERCHANTABILITY or FITNESS
 FOR A PARTICULAR PURPOSE. You are welcome to change and distribute
 copies under certain conditions. See the source for more information.
===========================================================================
M_Init: Init miscellaneous info.
R_Init: Init DOOM refresh daemon - [..........................]
P_Init: Init Playloop state.
I_Init: Setting up machine state.
NET_Init: Initialise network subsystem.
S_Init: Setting up sound.
D_CheckNetGame: Checking network game status.
startskill 2  deathmatch: 0  startmap: 1  startepisode: 1
player 1 of 1 (1 nodes)
Emulating the behavior of the 'Ultimate Doom' executable.
HU_Init: Setting up heads up display.
ST_Init: Init status bar.
I_InitGraphics: 320x200 mode not supported on this machine.
I_InitGraphics: Auto-adjusted to 640x400.
NOTE: Your video settings have been adjusted.  To disable this behavior,
set autoadjust_video_settings to 0 in your configuration file.
Killed

```

---

### Post by fragglet on 2010-08-14
Odd.  Does it make any difference if you run it windowed instead of full screen at all?

---

### Post by QwUo173Hy on 2010-08-15
I hadn't thought to try that! Yes actually, it runs great windowed. And I've been running prboom windowed so perhaps something on the desktop is interfering.

---

### Post by thatguruguy on 2010-08-15
Make sure you turn off any desktop effects (i.e., compiz)

---

### Post by QwUo173Hy on 2010-08-16
I have a seperate login for games, which is compiz-free. But I've been playing doom in my standard user account. Prboom is fine with it and I "think" that I did disable it when trying chocolate the second time around.

---

