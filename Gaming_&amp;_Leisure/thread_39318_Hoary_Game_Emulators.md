---
title: "Hoary Game Emulators"
date: 2005-06-04
forum: Gaming &amp; Leisure
---

### Post by mattblack_uk on 2005-06-04
I'm looking for a good Genesis emulator for Hoary, has anybody gotten one working ok? I know that Gens was a good one for use on Windows, but I can only find source available. Is there a deb package available anywhere as I'm not at all confident about compiling from source - I'm worried that I'll mess my system up.

 Thanks

---

### Post by mattblack_uk on 2005-06-04
As a Windows user I had a pile of good emulators as I enjoy retro gaming. Now I have moved over to Linux, I seem to be having a problem locating emulators for this and that. Basically what I'm asking is that if there are any emulation fans out there using Hoary, could you kindly give me a list of emulators which you have successfully got working in Hoary - preferably with a gui, although beggers can't be choosers!

I already know of xmame and snes9x & zsnes. What I'm looking for in particular are emulators for Amiga, AtariST, Commodore 64, Spectrum, Amstrad CPC464, Genesis, Master System. With the computer emulators, I'm not going to be doing anything else other than gaming.

Thankyou

---

### Post by bored2k on 2005-06-04
vice - The Versatile Commodore Emulator
uae - The Ubiquitous Amiga Emulator: Base
dgen - Sega Genesis/MegaDrive emulator
spectemu-common - Fast 48k ZX Spectrum Emulator (common files)
spectemu-svga - Fast 48k ZX Spectrum Emulator for SVGAlib
spectemu-x11 - Fast 48k ZX Spectrum Emulator for X11
xmess-x - X binaries for the Multi Emulator Super System

They are all in your repositories. There are plenty more, but I'm sure google will help you.

[http://www.mameworld.net/easyemu/mameguide/mamevariants.htm](http://www.mameworld.net/easyemu/mameguide/mamevariants.htm)

**Edit** - Do not double post.

---

### Post by Jormundgand on 2005-06-04
Amiga: uae
AtariST: hatari
Commodore: vice/xmess-x
Spectrum: spectemu-x11/xmess-x
Amstrad: none that I know of
Genesis: dgen/xmess-x
Master System: xmess-x

---

### Post by bored2k on 2005-06-04
On that note, anyone got CPS2 games working ? I never got it to work and the link is dead (I soo miss CPS2).

---

### Post by mattblack_uk on 2005-06-04
> Edit - Do not double post.

Sorry - I posted an initial thread about genesis emulators, then changed my mind and decided to start a new one on all emulators.

---

### Post by mattblack_uk on 2005-06-04
Thanks so far....

No Amstrad ones? Thats a shame as its what I used to have when I was younger - brings back a lot of memories.

Is UAE for linux difficult to configure?

---

### Post by mattblack_uk on 2005-06-04
DGen? Does that work OK? I thought they'd stopped development on that ages ago....

---

### Post by apollyonis on 2005-06-04
[QUOTE=bored2k]On that note, anyone got CPS2 games working ? I never got it to work and the link is dead (I soo miss CPS2).[/QUOTE]

What I've ended up doing for Arcade/CPS2/NeoGeo emulation is using AdvanceCD. Basically you have an option of making an .iso with whatever ROMs, screenshots, background music, etc. you want on a bootable CD/DVD or USB drive. This way I can take my games and a USB controller with me pretty much anywhere and play them that way too.  \\:D/  Get AdvanceCD   [here : Link](http://advancemame.sourceforge.net/index.html)

---

### Post by mattblack_uk on 2005-06-04
I've just installed VICE from the repositories.....

when i try and run x64, it gives me this:

> mark@ubuntu:~$ x64
*** VICE Version 1.14 ***

Welcome to x64, the free portable C64 Emulator.

Current VICE team members:
A. Boose, D. Lem, T. Biczo, A. Dehmel, T. Bretz, A. Matthies,
M. Pottendorfer, M. Brenner, S. Trikaliotis.

This is free software with ABSOLUTELY NO WARRANTY.
See the "About VICE" command for more info.

X11: Found 24bit/TrueColor visual.
X11: Using private colormap.
Xlib:  extension "XFree86-DGA" missing on display ":0.0".
DGA2: Error - Unable to query video extension version - disabling fullscreen.
C64MEM: Error - Couldn't load kernal ROM `kernal'.
Machine initialization failed.

Exiting...

Seems to be looking for XFree86-DGA, I thought Hoary used XOrg?

---

### Post by Wertigon on 2005-06-05
[QUOTE=mattblack_uk]As a Windows user I had a pile of good emulators as I enjoy retro gaming. Now I have moved over to Linux, I seem to be having a problem locating emulators for this and that. Basically what I'm asking is that if there are any emulation fans out there using Hoary, could you kindly give me a list of emulators which you have successfully got working in Hoary - preferably with a gui, although beggers can't be choosers!

I already know of xmame and snes9x & zsnes. What I'm looking for in particular are emulators for Amiga, AtariST, Commodore 64, Spectrum, Amstrad CPC464, Genesis, Master System. With the computer emulators, I'm not going to be doing anything else other than gaming.

Thankyou[/QUOTE]
 [http://www.zophar.net/unix/unix.phtml](http://www.zophar.net/unix/unix.phtml)

If they don't have it, chances are it doesn't exist.

---

### Post by meldroc on 2005-06-05
Don't forget about atari800, the Atari 8-bit emulator.  I've had pretty good luck using that one.

---

### Post by pierlo on 2005-06-06
nobody seems to have mentioned [epsxe](http://www.epsxe.com)  , a Playstation (1) emulator for linux.
It works fine (still havent tried personally on my ubuntu but i will soon) just follow [this howto](http://terror.snm-hgkz.ch/gaming/linux/epsxe_howto/) to get things working fine

(i know it's not retrogaming, still it adds lot of fun to your emu-box) :D

hope this helps

---

### Post by pierlo on 2005-06-07
just wanted to report my succesful attempt to get epsxe running.
anyway it's freeware, not opensource.
i would suggest another great opensource playstation emulator which is [PCSX](http://www.pcsx.net/) . 
Its main advantage is that it does not require a Psx bios ripped somehow (which is considered illegal if you do not own a Playstation or a PsOne) because the developers ship it with a custom bios (created by them i guess) which actually works ok.

For these two reasons, i wouldn't dislike to see PCSX inside the multiverse (or universe?) repositories... (i would love it actually!  :)  )

ciao

---

### Post by fastluck on 2005-06-09
I couldn't find vice anywhere.  I tried synaptic and apt-get.  None of the emulators mentioned in this thread show up--even when I use wildcards. But I was given the opportunity to install vic (a video-conferencing app).  What do I need to point to?

TIA

Fastluck

---

### Post by mattblack_uk on 2005-06-10
Vice is in the Universe repository....

---

### Post by fastluck on 2005-06-10
Thanks!

John

---

### Post by Kyral on 2005-06-10
I cannot find a BIOS for epsxe. Can anyone help me? (Can I even ask that here?)

Oh, and I do own a PSOne :P I'm just feeling too lazy to pull it out right now :P

---

### Post by fastluck on 2005-06-10
> C64MEM: Error - Couldn't load kernal ROM `kernal'.

You need to download the source and extract it.  Then copy everything under ...../data in the source to the same location where the binaries are installed.

I just realized I only got sound working for the c128. c64 doesn't give me any errors, but it also doesn't give me any sound.

Games are pretty sucky w/out sound!

---

### Post by ganatronic on 2005-06-11
I'm having trouble locating a graphical-interfaced nes emulator. Maybe I'm doing something wrong, but FCE Ultra  (from repository) seems to be terminal-only, as does Tuxnes. I've been struggling to master the commands, and I'd just love to be able to scroll through my games and then just load them up with a few clicks. 

Is there anything that's like zsnes, except without the first 's'?

I've found Gtuxnes, and Nintencer. But I couldn't get either to install (I know how to untar, configure, make, and then make install - and if that process doesn't work smoothly, I'm usually stuck). Nintencer is a current project, so I'll keep my eye on it.


and who would ever have guessed that owning 80 nes games as a kid would help to keep me a law-abiding citizen as a grown-up? ;)

---

### Post by ganatronic on 2005-06-14
Is there anyone who can answer the question I posed in the previous reply? I'm moving in a week, and will have very limited access to the internet. I'd love to have a solid nes emulator working before then.

nes emulator with gui?

---

### Post by fastluck on 2005-06-15
Check out this site:  [http://www.emuxhaven.net/nesemu.shtml](http://www.emuxhaven.net/nesemu.shtml).  And this one: [http://tuxnes.sourceforge.net/links.php](http://tuxnes.sourceforge.net/links.php).

Let us know what you find out, ok?  I'm interested too.

Fastluck

---

### Post by betrayed on 2005-06-15
[http://www.zophar.net/unix/nes.html](http://www.zophar.net/unix/nes.html)

If it isn't here good luck finding it.  As for the desire for a gui I don't see the need.  Fce ultra is in my opinion the best nes emulator around and a simple reading of the instructions shows how easy it really is to use.

[http://jturner.tapetrade.net/sharpnes/](http://jturner.tapetrade.net/sharpnes/) is another one some people have seemed to like.  I don't have the mono system installed so I can't try it

---

### Post by fastluck on 2005-06-15
I followed betrayed's posted link and found this: [http://rocknes.kinox.org/](http://rocknes.kinox.org/).

Fastluck

---

### Post by leech on 2005-06-15
Don't forget a great emulator of the AtariST

XSteem.  Unfortunately it's not packaged, but it runs pretty much everything you can throw at it.

Leech

---

