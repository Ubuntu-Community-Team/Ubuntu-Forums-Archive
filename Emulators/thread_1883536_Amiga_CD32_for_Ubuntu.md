---
title: "Amiga CD32 for Ubuntu ?"
date: 2011-11-19
forum: Emulators
---

### Post by honeybear on 2011-11-19
Hello,

Unfortunately for Linux Ubuntu, I do not think that Ubuntu emulates with any emulators Amiga CD32. Is it correct? 

You can with Wine, but a solution for Ubuntu would be possible with uae improved? 

Howto for Windows : 
[http://wiki.abime.net/emulation/winuae/cd32](http://wiki.abime.net/emulation/winuae/cd32)

:popcorn:

---

### Post by weasel fierce on 2011-11-20
> **honeybear said:**
> Hello,

Unfortunately for Linux Ubuntu, I do not think that Ubuntu emulates with any emulators Amiga CD32. Is it correct? 

You can with Wine, but a solution for Ubuntu would be possible with uae improved? 

Howto for Windows : 
[http://wiki.abime.net/emulation/winuae/cd32](http://wiki.abime.net/emulation/winuae/cd32)

:popcorn:

I must admit I have never tried it. A roundabout solution is to set up an emulated amiga hard drive, install software to run CD32 games and work from there. Not sure if it's worth the trouble though.

I use my A1200 for most amiga stuff these days, so Im not too up on amiga emulation anymore :)

---

### Post by honeybear on 2011-11-21
> **weasel fierce said:**
> I must admit I have never tried it. A roundabout solution is to set up an emulated amiga hard drive, install software to run CD32 games and work from there. Not sure if it's worth the trouble though.

I use my A1200 for most amiga stuff these days, so Im not too up on amiga emulation anymore :)

you do not have any PC? You are still using an Amiga ? 

It isnt too slow. YOu have workbench of the A500 and modem?

---

### Post by TenPlus1 on 2011-11-21
If you wish to emulate an Amiga CD32 which is basically an Amiga 1200 with a CD-Drive you can install uae or e-uae from synaptic or software centre to emulate the Amiga, but you WILL need an Amiga ROM to make it work...  Their are Amiga 500/600/1200/CD32 roms out there but you'll have to find them yourself if you do not already own a device...

As for the games, many sites provide image files for Amiga floppy games and the odd cd32 .iso image...

---

### Post by honeybear on 2011-11-21
> **TenPlus1 said:**
> If you wish to emulate an Amiga CD32 which is basically an Amiga 1200 with a CD-Drive you can install uae or e-uae from synaptic or software centre to emulate the Amiga, but you WILL need an Amiga ROM to make it work...  Their are Amiga 500/600/1200/CD32 roms out there but you'll have to find them yourself if you do not already own a device...

As for the games, many sites provide image files for Amiga floppy games and the odd cd32 .iso image...

could you please help us knowing how you load the cdrom into e-uae? it is only for ADF or ZIP

---

### Post by weasel fierce on 2011-11-21
> **honeybear said:**
> you do not have any PC? You are still using an Amiga ? 

It isnt too slow. YOu have workbench of the A500 and modem?

I do use my PC for day to day stuff, the amiga is for classic games, though it also works for email (YAM for the win), IRC chat and other little things.

Its an A1200 with wireless PCMCIA card, 64 megs of RAM and a 68030/56 mhz

---

### Post by TenPlus1 on 2011-11-26
This may help: [http://cshandley.co.uk/runinuae/](http://cshandley.co.uk/runinuae/)

---

### Post by honeybear on 2011-12-21
> **weasel fierce said:**
> I do use my PC for day to day stuff, the amiga is for classic games, though it also works for email (YAM for the win), IRC chat and other little things.

Its an A1200 with wireless PCMCIA card, 64 megs of RAM and a 68030/56 mhz

thats cool

are the graphics cool and awesome colors with amiga? 

I think that amiga had amazing colors, like rainbow, and still regular pc or games cannot offer nowadays. Some demo or games are still today amazing panel of colors and graphics

---

### Post by weasel fierce on 2011-12-21
I like it. THere's a certain sort of style to it.
One of the nicest things is how smooth scrolling is, considering the limited hardware. 
There's really nothing like loading up Agony on an A500 with its 7 mhz processor to make people's jaws drop.

---

### Post by honeybear on 2011-12-23
> **weasel fierce said:**
> I like it. THere's a certain sort of style to it.
One of the nicest things is how smooth scrolling is, considering the limited hardware. 
There's really nothing like loading up Agony on an A500 with its 7 mhz processor to make people's jaws drop.

wow [http://www.youtube.com/watch?v=WYxIJxqrv6U&feature=related](http://www.youtube.com/watch?v=WYxIJxqrv6U&feature=related)

---

### Post by FrodeSolheim on 2012-05-01
> **honeybear said:**
> Hello,

Unfortunately for Linux Ubuntu, I do not think that Ubuntu emulates with any emulators Amiga CD32. Is it correct? 


I'm a bit unsure of the status of CD32 emulation in the older UAE versions, but FS-UAE supports CD32 emulation (same CD32 emulation code as WinUAE).

I run it myself on Ubuntu (just note that with 12.04 and 3D-accelerated desktop, you may need to run FS-UAE in fullscreen or with the option --video-sync=off to get good performance due to a Compiz issue).

If you try it out and have any problems, just let me know.

[http://fengestad.no/wp/fs-uae](http://fengestad.no/wp/fs-uae) (I provide precompiled Ubuntu/Debian debs).
[]("http://fengestad.no/wp/fs-uae")

---

### Post by schtufbox on 2012-05-02
Just out of curiosity, can FS-USE open zipped ADF files? or so they need to be unzipped?

--edit, never mind, checkecked myself..it does :)  However is there any way to choose a disk to load without editing the config file every time?  It never lists the adf files (zipped or unzipped) in the default folder...

---

### Post by FrodeSolheim on 2012-05-02
> **schtufbox said:**
> Just out of curiosity, can FS-USE open zipped ADF files? or so they need to be unzipped?

--edit, never mind, checkecked myself..it does :)  

Yes, and it also supports gzipped ADF (adz) as well as IPF and DMG disk images.

> **schtufbox said:**
> However is there any way to choose a disk to load without editing the config file every time?  It never lists the adf files (zipped or unzipped) in the default folder...

Not currently, no. FS-UAE is designed to be started with (for instance) a configuration file per game (either created manually, or created on-demand by a frontend / external configuration program). You can give the path to the configuration as a parameter to fs-uae.

I am also working on a graphical launcher, which will remove the need to manually fiddle with configuration files. This post has a screenshot and more information: [http://eab.abime.net/showpost.php?p=815068&postcount=197](http://eab.abime.net/showpost.php?p=815068&postcount=197)

---

### Post by FrodeSolheim on 2012-05-02
There is also an unofficial FS-UAE launcher/GUI for Linux here (which supports all FS-UAE options, according to the author):
[http://eab.abime.net/showthread.php?t=63971](http://eab.abime.net/showthread.php?t=63971)
[http://sourceforge.net/projects/gfsuae/](http://sourceforge.net/projects/gfsuae/)

---

### Post by schtufbox on 2012-05-02
Thanks, that's just what I need :)

---

### Post by FrodeSolheim on 2012-11-01
> **schtufbox said:**
> However is there any way to choose a disk to load without editing the config file every time?  It never lists the adf files (zipped or unzipped) in the default folder...

Hi, FS-UAE 2.0 now includes FS-UAE Launcher, a convenient frontend for FS-UAE, so there is no need to edit configuration files any more.

FS-UAE + FS-UAE Launcher are now even available from an Ubuntu PPA :):
[http://fengestad.no/fs-uae/download](http://fengestad.no/fs-uae/download)

---

### Post by WienerWuerstel on 2012-11-02
> **FrodeSolheim said:**
> Hi, FS-UAE 2.0 now includes FS-UAE Launcher, a convenient frontend for FS-UAE, so there is no need to edit configuration files any more.

FS-UAE + FS-UAE Launcher are now even available from an Ubuntu PPA :):
[http://fengestad.no/fs-uae/download](http://fengestad.no/fs-uae/download)
I agree! FS-UAE 2.0 + Launcher is probably the best and most convenient way to play Amiga Games on your Ubuntu Box.

---

### Post by honeybear on 2012-11-03
> **WienerWuerstel said:**
> I agree! FS-UAE 2.0 + Launcher is probably the best and most convenient way to play Amiga Games on your Ubuntu Box.

is it into apt-get ?

or one must get the debs.

which software/game would you advice that work with it?


Does it work with console/bash for mythtv setup with lirc and remote controler?

---

### Post by WienerWuerstel on 2012-11-03
> **honeybear said:**
> is it into apt-get ?

or one must get the debs.

which software/game would you advice that work with it?


Does it work with console/bash for mythtv setup with lirc and remote controler?

You need to add the PPA and then you can install it via apt-get. Which only takes 3 Terminal Commands.
```
sudo apt-add-repository ppa:fengestad/stable 
sudo apt-get update 
sudo apt-get install fs-uae fs-uae-launcher
```Every Amiga Game should work with it. I tested Games like Turrican, Space Harrier, Double Dragon and Flashback. 
Software should work too but I don't know any Programs that were made for the Amiga so I couldn't test it.

And I don't know if it would work with your mythtv setup as I have no clue on how mythtv works and never had any use for it in the first place.

---

### Post by honeybear on 2012-11-03
> **WienerWuerstel said:**
> You need to add the PPA and then you can install it via apt-get. Which only takes 3 Terminal Commands.
```
sudo apt-add-repository ppa:fengestad/stable 
sudo apt-get update 
sudo apt-get install fs-uae fs-uae-launcher
```Every Amiga Game should work with it. I tested Games like Turrican, Space Harrier, Double Dragon and Flashback. 
Software should work too but I don't know any Programs that were made for the Amiga so I couldn't test it.

And I don't know if it would work with your mythtv setup as I have no clue on how mythtv works and never had any use for it in the first place.

thank you so much !

there are simply too much different uae version.

Actually they should also support Ubuntu (debs) on their site:
[http://fengestad.no/fs-uae/download](http://fengestad.no/fs-uae/download)

They should really think one day about merging. Look for instance  ***gens***, that is a really great emulator.

---

### Post by WienerWuerstel on 2012-11-03
> **honeybear said:**
> thank you so much !

there are simply too much different uae version.

Actually they should also support Ubuntu (debs) on their site:
[http://fengestad.no/fs-uae/download](http://fengestad.no/fs-uae/download)

They should really think one day about merging. Look for instance  ***gens***, that is a really great emulator.

No Problem ;)

Well I don't think there are too many UAE Versions. UAE and E-UAE ar dead anyways so there are only 2 UAE Version for Linux out there that are still alive and well. PUAE and FS-UAE

And also it would make no sense to merge with a dead Project when the one that you have is already a lot better.

PS: gens is a good Emulator but Kega Fusion is better imo

---

### Post by honeybear on 2012-11-03
> **WienerWuerstel said:**
> No Problem ;)

Well I don't think there are too many UAE Versions. UAE and E-UAE ar dead anyways so there are only 2 UAE Version for Linux out there that are still alive and well. PUAE and FS-UAE

And also it would make no sense to merge with a dead Project when the one that you have is already a lot better.

PS: gens is a good Emulator but Kega Fusion is better imo

Over 10 years, I cannot even remember how much versions or extensiosn of UAE I hve been using... 

Hoping that soon or later we get to a cool single UAE one ;) very probably it will ;) :guitar:

---

### Post by FrodeSolheim on 2012-11-05
> **honeybear said:**
> Actually they should also support Ubuntu (debs) on their site:[ http://fengestad.no/fs-uae/download]("http://fengestad.no/fs-uae/download")
That PPA is the official PPA for FS-UAE, and is listed on the download page, along with direct download of deb files...

> **honeybear said:**
> They should really think one day about merging.

Well, the original UAE and E-UAE have not been developed for years. When it comes to the emulation code itself, FS-UAE is very closed synced with WinUAE (which is where the real progress in emulation is happening). The latest FS-UAE development version uses the emulation core from WinUAE 2.5.0beta23 and I have just merged the WinUAE 2.5.0beta24 changes. I have also made some code patches which are incorporated in WinUAE which makes more of the WinUAE code compilable with GCC, so there is some cooperation going on. I wouldn't worry that much about merging as such. The important thing is code sharing.

> **honeybear said:**
> Hoping that soon or later we get to a cool single UAE one :wink: very probably it will :wink: :guitar:
I think FS-UAE is pretty cool (but I'm biased), and it is actively developed so it will be even better :)

---

### Post by honeybear on 2013-03-06
Hi, 

Fs-uea look snice but youwould know if those ones could eventually work?

rgds

apt-cache search uae
tiemu - Texas Instruments calculators emulator (without GDB)
e-uae-dbg - The Egalitarian Ubiquitous Amiga Emulator (debugging)
e-uae - The Egalitarian Ubiquitous Amiga Emulator
uae-dbg - The Ubiquitous Amiga Emulator (debugging)
uae - The Ubiquitous Amiga Emulator

---

### Post by honeybear on 2013-03-06
Hi, 

Fs-uea look snice but youwould know if those ones could eventually work?

rgds

apt-cache search uae
tiemu - Texas Instruments calculators emulator (without GDB)
e-uae-dbg - The Egalitarian Ubiquitous Amiga Emulator (debugging)
e-uae - The Egalitarian Ubiquitous Amiga Emulator
uae-dbg - The Ubiquitous Amiga Emulator (debugging)
uae - The Ubiquitous Amiga Emulator

---

### Post by Linuxgamer94 on 2013-07-31
Gens and Kfussion are dead on Linux. Also have you tried AEROS or AROS. They are both free and while you would have to duel boot. They also have Amiga OS 4.2 out now and the more cheaper Morph OS. Man those Amiga OS users pay as Much if not more then an average Mac user does.

---

