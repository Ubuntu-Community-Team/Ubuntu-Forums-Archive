---
title: "apple ][ emulator help"
date: 2009-03-08
forum: Gaming &amp; Leisure
---

### Post by syntacsugar on 2009-03-08
hi

so i'm really tyring to learn 6502 assembly and i just got a book on apple ][ assembly today. and i remember seeing something about the xapple emulator . i downloaded it with synaptic. and when i go to the terminal to run it i get this message.


Warning. Cannot open the .apple2 system defaults file.
Make sure it's readable in your home directory.Press RETURN to continue...
ioperm: Operation not permitted
cannot get port access to PC speaker.
sound will not be used.
Using standard VGA 320x200 mode.
Press RETURN to continue...
svgalib: Cannot get I/O permissions.
Warning. Cannot open the .apple2 system defaults file.
Make sure it's readable in your home directory.Press RETURN to continue...
Sorry bud, xapple2 only supports 8bit PseudoColor displays.
Maybe you can fix this!

how can i fix this? are there any other apple 2 emulators around?

thanks

---

### Post by patrick295767 on 2009-03-17
> **Exilim said:**
> There are many Free Apple II, II plus, IIe, IIc, IIgs Emulators at this site: [http://www.thefreecountry.com/emulators/apple-2.shtml](http://www.thefreecountry.com/emulators/apple-2.shtml)

NO Linux emulators, except xapple2 on your url
You link is for Windows:[www.microsoft.com/](www.microsoft.com/)

This forum is LINUX.
here is the linux: [http://www.linux.org/](http://www.linux.org/)

anyhow, thx

---

### Post by DoktorSeven on 2009-03-17
The other thread mentioned KEGS ([http://kegs.sourceforge.net/](http://kegs.sourceforge.net/)) as an IIgs emu that can run II/IIe/etc stuff.  Haven't tried that, but beyond that I do not know of a II-series emulator that easily runs on modern Linux (as you've seen with xapple2 it needs 8-bit displays!).  

My solution for Apple II is to run a Windows program via Wine, though that's not an optimal solution, I know.

---

### Post by patrick295767 on 2009-03-17
> **DoktorSeven said:**
> The other thread mentioned KEGS ([http://kegs.sourceforge.net/](http://kegs.sourceforge.net/)) as an IIgs emu that can run II/IIe/etc stuff.  Haven't tried that, but beyond that I do not know of a II-series emulator that easily runs on modern Linux (as you've seen with xapple2 it needs 8-bit displays!).  

My solution for Apple II is to run a Windows program via Wine, though that's not an optimal solution, I know.

well, I dont want to use wine nor windows.
So, try this:

sudo xapple2
and install the svgalibs

you see, you get something :)

---

### Post by DoktorSeven on 2009-03-17
Running an emulator (or in fact any program like that) as root isn't a very good idea.

What needs to happen is someone need to take sources and make a modern apple2 emulator that can run without such hackery.

---

### Post by patrick295767 on 2009-03-17
> **DoktorSeven said:**
> Running an emulator (or in fact any program like that) as root isn't a very good idea.

What needs to happen is someone need to take sources and make a modern apple2 emulator that can run without such hackery.

it was an example to get the vgalibs working
one can setup it

eg zgv can displays images without X !!!

---

### Post by everdred on 2009-04-08
> **patrick295767 said:**
> and install the svgalibs


Which package, in particular? I tried just about everything svgalib* in the repository, to no avail.

---

### Post by Grishka on 2009-04-10
kegs runs well, but it only emulates apple IIgs, and won't run programs for other models. xapple2 doesn't work.
sdlmess is the only reliable option for emulating old apple microcomputers, but it's not exactly comfortable to set up, and it looks like there's no way to change disks ingame. or I can't find one. but at least it loads .nibs and emulates all apple models. it's in ubuntu repos, but it's outdated. get the new version from: [http://rbelmont.mameworld.info/?page_id=163](http://rbelmont.mameworld.info/?page_id=163). there's a link to a debian repo, it works with ubuntu as well. also, a few frontends are available, though they only partially ease the installation. are you butch enough to tame this beast? ;)

---

