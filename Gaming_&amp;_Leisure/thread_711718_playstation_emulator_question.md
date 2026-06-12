---
title: "playstation emulator question"
date: 2008-02-29
forum: Gaming &amp; Leisure
---

### Post by 900donuts on 2008-02-29
is there a playstation emulator that doesn't need a bios dump?

---

### Post by piratesmack on 2008-02-29
nope sorry

---

### Post by 900donuts on 2008-02-29
what about pcsx? (i'm trying to confirm a wikipedia claim)

---

### Post by XSP on 2008-03-01
PCSX internally emulated the BIOS. I have no idea how well it ran however.

---

### Post by 900donuts on 2008-03-01
i used synaptic  to get pcsx-df which seems to work how do i get it to run a disc?

---

### Post by piratesmack on 2008-03-01
hm that's pretty cool, I always though pcsx needed a bios dump so i never tried it  without one. I've always been more of a epsxe guy, though. I don't think the default CD plugin for PCSX lets you run CDs, only ISO's. So you'll probably have to find another cd plugin or use epsxe

---

### Post by acoustibop on 2008-03-01
AIR the internal BIOS in PCSX never worked very well.  Connectix VGS (one of the earliest Playstation emulators; even older than PCSX!) had one that worked pretty well, and Xebra (I think in its Arbex version) has one - this is also said to be good.  However, these emulators  are both Windows only.

Fortunately, I have the BIOS I ripped from my Playstation (which I still have - and is still working) many years ago.  Does me for pSX Emulator which, to my mind, far the best solution for Linux, in performance, ease of installation and compatibilty.

However, Playstation BIOSs are not difficult to find with google - you should bear in mind that downloading them is illegal in most countries, though.

---

### Post by UK-Wobbie on 2008-03-01
> **900donuts said:**
> is there a playstation emulator that doesn't need a bios dump?

The bios is the system of the playstation so what ever you like to emulate you need a bios.

---

### Post by 900donuts on 2008-03-01
i have a play station here how do i dump the bios?

---

### Post by acoustibop on 2008-03-01
See Shendo's [PSX BIOS Dumping guide]("http://forums.ngemu.com/misc-psx-discussion/93161-psx-bios-dumping-guide.html") in the NGEmu Emuforums, 900donuts.  Note that all BIOS dumping methods involve the use of extra hardware - a DexDrive here, or a GameShark type device (not the CD, the kind that plugs into a Playstation and can be used to connect it to a PC's serial port, for another method.

Note that only older Playstations that have a serial I/O port and PCs that have a serial port can be used for the second method.  AFAIK Shendo's method should work with any Playstation.

**Edit:** no, that's not quite true: your Playstation will need to be able to boot burned CDs, which generally means it'll have to be chipped.

---

### Post by BigSilly on 2008-03-01
Acoustibop - I've got a quick quessie for you. I think I remember you helping me out before with pSX. Please excuse me for picking your brains again!

I'm currently trying to get pSX to run on my Mandriva 2008 Powerpack install. I've got all the dependencies and the requisite BIOS file, but it doesn't seem to work. Bear in mind that it runs beautifully on my main Ubuntu install. If I cd into the directory, then type ./pSX, a dialogue box to select the language pops up. I select "English", then I get:

```
pad=0
Segmentation fault
```

Can you recommend anything I can do to fix this? Thanks very much in advance.

---

### Post by eragon100 on 2008-03-01
I don't have a playstation, and i though i couldn't play games on pscx without one, since wikipedia mentions it's illegal. Great news :guitar:

---

### Post by acoustibop on 2008-03-01
Well, as long as the big console developers actively try to prevent their consoles being emulated, eragon100, that's how it is.

Personally, I think it's just one more demonstration of the total lack of intelligence and humanity on the part of big media companies.  Having turned most of their product into profit oriented cr*p, and messed their consumer base around royally - what about Sony's attempts to protect their CDs by installing rootkits on people's machines? - they then wonder why there's such a prevalence of piracy...

We all have to find our own solutions - just remember google is your friend...

@BigSilly: I don't really know much about Mandriva.  Is yours a 32bit or a 64bit OS, and are your Linux and Mandriva installations on the same machine?

---

### Post by 900donuts on 2008-03-01
so how do i chip the playstation? it a scph-9001(preferably solder free)

p.s. is there any gadgets for dumping snes carts?(i have a few laying around)

---

### Post by disturbedite on 2008-03-01
there are legit places you can take or send your playstation (or other consoles) to get it/them modded (chipped).

there are "gadgets" for duming carts of all kinds.  i hear ebay is a great place to find them.

---

### Post by BigSilly on 2008-03-01
> **acoustibop said:**
> 
@BigSilly: I don't really know much about Mandriva.  Is yours a 32bit or a 64bit OS, and are your Linux and Mandriva installations on the same machine?

Hi there. Yes, I'm currently using both Ubuntu 7.10 and Mandriva 2008 on the same machine, and it's a 32bit PC. It's not really a problem, since as I say it plays wonderfully on Ubuntu, but it would be nice to be able to use it when I'm on Mandriva, and I like getting stuff to work on Linux. You can't beat the sense of achievement, plus you get to add another string to your Linux bow. ;)

If anyone has any experience of this problem and can help that would be great. Cheers all, and thanks for your response Acoustibop! :)

---

### Post by Faud on 2008-03-02
Would it really be as easy as sticking it one of my playstation cd's in the drive and hitting run ? or would it be a lot of work to try and play the ps games on ubuntu ?

---

### Post by acoustibop on 2008-03-02
With pSX, it's pretty much that on Ubuntu, Faud.  You need to install libgtkglext1 (in the repositories), have a properly working 3D videocard and soundcard, and to have a Playstation BIOS (which you stick in the bios folder after you've decompressed the [pSX download]("http://psxemulator.gazaxian.com/")).

Then you download the pSX tar.bz2, decompress it wherever you want - your home folder is favourite - put your BIOS into the bios folder, run the pSX executable and add games - CDs or images - to taste.  You'll probably want to configure your controller if you have one, but that's about all the configuration you really need to do.

Bear in mind that you may get issues with games that are copy or mod protected and, as with all emulators, there may be games that have compatibility problems.  Many of the issues can be worked round, though - pSX is very good at defeating protection given a drive that reads the subcode sectors - most games are not protected - and has very good compatibilty now, possibly the best of any Playstation emulator, although Xebra (a Windows-only emulator) may be a bit better.

@BigSilly: it might be an idea to post your problem on the [official pSX forum]("http://psxemulator.proboards54.com/"), or the Mandriva ones.

---

### Post by BigSilly on 2008-03-02
> **acoustibop said:**
> 
@BigSilly: it might be an idea to post your problem on the [official pSX forum]("http://psxemulator.proboards54.com/"), or the Mandriva ones.

Yup, will do. I thought it might be a generic Linux problem, rather than a distro-specific one, but as it's looking like that I'll post it up on the Mandriva forums. Cheers 'cousti. :)

---

### Post by disturbedite on 2008-03-02
dfreer has a repo with pSX in it.  no need to download it & "manually" install it when he has deb packages for ubuntu available.

---

### Post by acoustibop on 2008-03-02
True, disturbedite, but many people, myself included, prefer to just install in our Home folders.  That way, we can install as many versions as we like simultaneously.  Also, with versions of pSX before the current one, 1.13, the configuration file would be written to the same folder as the executable, which made it a bit awkward for manually editing it.  Whatever works for you, I guess... ;)

---

