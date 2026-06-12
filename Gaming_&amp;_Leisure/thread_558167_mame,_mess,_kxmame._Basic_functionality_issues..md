---
title: "mame, mess, kxmame. Basic functionality issues."
date: 2007-09-23
forum: Gaming &amp; Leisure
---

### Post by rybu on 2007-09-23
Hi there.  I've been fascinated by the possibility of playing old Vectrex games on my laptop.  So I installed kxmame in the hope that I could get the Vectrex roms to load and run.  So far I'm not having any luck. 

FYI: when you install kxmame using aptitude or synaptic, it sets it up with non-existant directories.  Specifically, if you go to the "Mame/Mess basic paths" in the directories config, it is trying to use /usr/lib/games/xmame/* for samples, artwork, BIOS and ROMs.  So I reconfigured those directories to point somewhere more useful, and installed some more useful items:

The Vectrex bios is available here: (as well as bios scans for many other old popular systems)

[http://www.emunews.eu/mess.htm](http://www.emunews.eu/mess.htm)

Overlays and Vectrex ROMs are available here:

[http://vectrex.classicgaming.gamespy.com/](http://vectrex.classicgaming.gamespy.com/)

But I haven't been able to get kxmame to "see" these games.  I mean, it's like kxmame has a "fixed" list of games, and the Vectrex games aren't on it.  The kxmame gamelist file isn't a text file so it's not clear how to add games to the list. Or is there an easier way to run these vectrex games?

I have been able to get some of the games working that are already on the kxmame list.  Things like "Star Fire".  Ugh, that's a boring game.

---

### Post by DoktorSeven on 2007-09-23
Well, I have kxmame 2 installed (for sdlmame) but I was able to get it working with xmess and Vectrex fine.  After setting the path to xmess in Settings->Directories  (Xmame/Xmess executables), switch to Xmess with Settings->Executable->Xmess.  If it doesn't do so automatically, System->Rebuild System List.  (Of course, also add the path to the BIOS (Settings->Directories, Mame/Mess Basic Paths tab, Mess BIOS path.)

You should be able to select Vectrex on the left, and navigate to a ROM on the right (via a directory listing).

This may all be different in kxmame2 from the kxmame in the repos, so adjust if necessary, or download/compile/install kxmame2 from its sourceforge site.

---

### Post by rybu on 2007-09-23
Thanks.  I just checked out the kxmame subversion tree.   The trunk/README file mentions that loading a foreign BIOS is a new feature to kxmame 2.  So I guess I'll be trying it out...

oh.  But I just checked out the version that was installed via synaptic -- version 2.  So I must be doing something wrong...

Okay, I didn't have xmess installed.  Now I have it installed, but kxmame doesn't offer mess as a viable executable. Only xmame (SDL) 0.106 appears.

Baby steps.

---

### Post by rybu on 2007-09-23
Woohoo!  

I got mine storm to work.   Things are looking up. 

So here's what I had to do so far:

In synaptic, install: kxmame, xmame-common, xmame-sdl, xmame-tools, xmess-common and xmess-sdl.  Do not install xmess-x as it conflicts with kxmame. 

Then run kxmame, and add xmess to the "Xmame/Xmess executables" directory in the directories setting under kxmame paths. 

Then do as DoctorSeven suggested: find the roms you want to use, put them in which ever directory you want.  But make sure they are all entered in the appropriate paths under directories -> mame/mess basic paths. 

Then change your executable to mess, under settings -> executable.  

Now I want to see if I can get any other games running. I'm getting funny error messages about duplicate ROMs if I try to play other vectrex games.

Here is the error message:

```

Kxmame could not create a device option for the selected rom "ARMOR.BIN" for the system "Vectrex".

This error is usually due to either this system doesn't need a rom (bios only mode), or the file is not a valid rom for this system, or it is in a format that kxmame or xmess doesn't understand.

How would you like to continue?

Run xmess with bios only

Run xmess, use the rom without a device option

```

The 1st option gives minefield, the 2nd option gives:

```
error: duplicate gamename: /home/rybu/.xmess/roms/ARMOR.BIN
```

---

### Post by rybu on 2007-09-23
This package could really use some decent documentation. 

It's not clear to me what the correct syntax of the xmess.SDL executable is, but as of yet I clearly don't understand it:

```

rybu@rybu-laptop:~/.xmess/roms$ xmess.SDL vectrex -cart BERZERK.BIN 
warning: no mixer plugins available
info: trying to parse: /etc/xmame/xmessrc
error: unknown option sysinfo_file, on line 11 of file: /etc/xmame/xmessrc
   ignoring line
error: unknown option messinfo_file, on line 12 of file: /etc/xmame/xmessrc
   ignoring line
error: unknown option fuzzycmp, on line 30 of file: /etc/xmame/xmessrc
   ignoring line
error: unknown option skip_disclaimer, on line 32 of file: /etc/xmame/xmessrc
   ignoring line
info: trying to parse: /home/rybu/.xmess/xmessrc
info: trying to parse: /etc/xmame/xmess-SDLrc
info: trying to parse: /home/rybu/.xmess/xmess-SDLrc
info: trying to parse: /etc/xmame/rc/vectrexrc
info: trying to parse: /home/rybu/.xmess/rc/vectrexrc
xmame: could not connect to socket
xmame: No such file or directory
LIRC disabled
loading rom 0: system.img                      
done
system.img   NOT FOUND
ERROR: required files are missing, the game cannot be run.
rybu@rybu-laptop:~/.xmess/roms$ 

```

---

### Post by disturbedite on 2007-09-23
please, please ppl don't use xmame.  its dead and has been since mame 0.106 and mame is currently at 0.119+!  try kxmame (2.0-svn-sdlmame-20070603 (which is available on the kxmame site) along with sdlmame.  sdlmame is actively developed and up-to-date.

---

### Post by rybu on 2007-09-23
I am using kxmame, xmess.SDL and xmame.SDL.  I mention it in my post.

---

### Post by fart_flower on 2007-09-23
> **rybu said:**
> I am using kxmame, xmess.SDL and xmame.SDL.  I mention it in my post.

Xmess.SDL and xmame.SDL are different from sdlmame and sdlmess.  The former are old and crusty, the latter are new and shiny.  As stated above, please avoid using the older ports -- they are no longer being updated.

---

### Post by rybu on 2007-09-23
That's nuts. 

So in the Ubuntu repository we have a defunct version of an emulator, which just happens to have almost the same name as a working version, which is *not* in the repository.   It all doesn't make sense in a very systematic way...

---

### Post by rybu on 2007-09-23
sdlmess and sdlmame do not have subversion repositories.  At present, they can be found on this webpage:

[http://rbelmont.mameworld.info/?page_id=163](http://rbelmont.mameworld.info/?page_id=163)

Right now sdlmame 0119u1 is compiling, so far so good... that worked.

sdlmess compiling seems to be going well... oop. problem. This is probably a 64-bit architechture problem...

```

src/emu/cpu/x86drc.c:714: warning: cast from pointer to integer of different size
src/emu/cpu/x86drc.c:717: warning: cast from pointer to integer of different size
/tmp/cchpg99j.s: Assembler messages:
/tmp/cchpg99j.s:49: Error: suffix or operands invalid for `push'
/tmp/cchpg99j.s:49: Error: suffix or operands invalid for `pop'
make: *** [obj/sdl/mess64/emu/cpu/x86drc.o] Error 1

```

---

### Post by disturbedite on 2007-09-24
> **rybu said:**
> That's nuts. 

So in the Ubuntu repository we have a defunct version of an emulator, which just happens to have almost the same name as a working version, which is *not* in the repository.   It all doesn't make sense in a very systematic way...
you are absolutely right, yes that IS the case and it is nuts.

---

### Post by fart_flower on 2007-09-24
The names aren't as silly as they could be.  For example, the names "xmame" (defunct *nix port) and "mame-x" (Xbox port) cause far more confusion.

At any rate, I've no idea why Ubuntu includes xmame in it's repositories instead of the actively updated sdlmame.  More than likely it's simply because very few people use emulators on Linux.  Users are far more worried about wireless cards, ACPI, playing DVDs out of the box, desktop effects, etc..

---

### Post by rybu on 2007-09-24
Okay, so I've finally got sdlmame and sdlmess working.  I can now play vectrex games with sdlmess in Ubuntu 7.10. 

Here is what I did:

Step 1, download sdlmame and sdlmess from: [http://rbelmont.mameworld.info/?page_id=163](http://rbelmont.mameworld.info/?page_id=163)  Yes, it's a website.  People tell me there's a subversion repository for sdlmess, here: 
svn://messdev.fdns.net/mess/ but I've tried to download from it every day for the past 3 days without success.  There is no repository for sdlmame, other than the above webpage. 

Step 2: unzip the packages in a directory.  The zip package puts them into appropriately-named subdirectories.

Step 3: enter the subdirectories.  In the mess directory type```

make -f makefile.sdl PTR64=1 -j3

``` this is for a 64-bit platform.  In the mame directory type ```
make -f makefile PTR64=1 -j3
```.  These two commands produce an executable called "mess" and "mame" respectively.  

Step 4: In some directory pointed to in your PATH variable, put symbolic links to the above mess and mame files. 

Step 5: ```
 mess vectrex -cart roms/vectrex/BERZERK.BIN -nomouse

``` is what I type to load up the vectrex game berzerk. This is in a directory which has the vectrex roms in the subdir roms/vectrex.  Similarly for other games, etc.  The -nomouse option is important in full-screen mode, otherwise I lose the mouse cursor when I leave mess (press ESC) and I have to restart X. 

Anyhow, I don't fully understand where mess is "looking to" to find various files but now all the basic vectrex games work on my laptop.  I'm a happy camper. 


Below are links to the two threads on an emulation message-board where I learned how to do all this stuff:

[http://www.bannister.org/forums/ubbthreads.php?ubb=showflat&Number=33927&page=1#Post33927](http://www.bannister.org/forums/ubbthreads.php?ubb=showflat&Number=33927&page=1#Post33927)

[http://www.bannister.org/forums/ubbthreads.php?ubb=showflat&Number=28714&page=1#Post28714](http://www.bannister.org/forums/ubbthreads.php?ubb=showflat&Number=28714&page=1#Post28714)

---

### Post by disturbedite on 2007-09-24
> **fart_flower said:**
> At any rate, I've no idea why Ubuntu includes xmame in it's repositories instead of the actively updated sdlmame.

actually, i believe its cuz the process that packages have to go through to get in the official repos is so rigorous, a lot of them don't make the cut...

---

### Post by fart_flower on 2007-09-24
Or maybe it's just as simple as nobody volunteering to step forward to  champion the cause of SDLMAME in Ubuntu.

---

### Post by disturbedite on 2007-09-25
> **fart_flower said:**
> Or maybe it's just as simple as nobody volunteering to step forward to  champion the cause of SDLMAME in Ubuntu.
i'm not saying this cuz i have to be right, but i know that is not the case.  the author has tried.  what i said is the case.

---

### Post by rybu on 2007-09-25
> **disturbedite said:**
> i'm not saying this cuz i have to be right, but i know that is not the case.  the author has tried.  what i said is the case.

Having looked at the code myself, it needs a *lot* of work to be ready for inclusion in a distribution.  Poor code documentation, a hacked makefile (not using automake), simple changes in the compiler options like level of optimization can break the binary...  no test suite... no subversion repository (there supposedly is one for sdlmess but I haven't been able to use it so far)...

I think it's a great project but if it's going to get out of the "hackers only" basement, it'll take serious work.

---

### Post by fart_flower on 2007-09-25
> **disturbedite said:**
> i'm not saying this cuz i have to be right, but i know that is not the case.  the author has tried.  what i said is the case.

Lighten up.  I wasn't cutting you down, just making a guess of my own.

---

### Post by fart_flower on 2007-09-25
> **rybu said:**
> Having looked at the code myself, it needs a *lot* of work to be ready for inclusion in a distribution.

Yeah, but how does it compare to xmame?

---

### Post by disturbedite on 2007-09-26
> **fart_flower said:**
> Lighten up.  I wasn't cutting you down, just making a guess of my own.
i didn't mean that in a harsh way, so yeah...

---

### Post by Rounin on 2009-04-08
I've had the same experience as rybu trying to use XMESS in Ubuntu. The version of the emulator included in Ubuntu is definitely quite unusable. Despite necessarily being a graphical application, since it runs games, the emulator is started from the command line, for some reason, and there's no apparent command that will cause the emulator to start or to run a game. Using kxmame causes the aforementioned error message about bioses and device configurations, which leads to it either doing nothing, or complaining about a duplicate game name, depending on what one chooses.

One has to wonder whether there's an active package maintainer for these packages, because it doesn't seem like they could have an active userbase which actually plays games with them. If the developers themselves manage to use them for anything, that's good for them, but they're definitely not ready to be shared with other users. It's especially frustrating considering how well MAME already worked on our old Macintosh several years ago.

---

### Post by wingnux on 2009-04-08
You could always go for sdlmame which works like a charm and it's up to date with the current mame build.

---

### Post by Rounin on 2009-04-08
Ah, yes, that does work! This version is rejected by kxmame, so we're back to the Kafka-esque command line, and by default there's [s]no[/s]glitchy sound, but it's hopefully something that can be solved by tweaking some config files. Thanks a lot for recommending this.

The audio problem seems to be associated with SDL and not with sdlmess, so it should be safe to include sdlmame and sdlmess in Ubuntu's repositories instead of xmame and xmess.

---

### Post by wingnux on 2009-04-08
sdlmame has a nice built-in game/rom browser but if you don't like it you can always use the Wah!Cade front-end, that's what I do ;)

---

