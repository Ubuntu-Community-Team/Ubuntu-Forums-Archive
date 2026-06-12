---
title: "Legend of Dragoon has the same problem in pSX /ePSXe. Can't get past 'SCEA Presents'"
date: 2008-05-16
forum: Gaming &amp; Leisure
---

### Post by Scrubzilla on 2008-05-16
My laptops's windows hard drive completely (physically) failed last week, so I decided to buy a new one and give ubuntu a whirl. 
I've been mostly sucessful in solving issues on my own, but I can't seem to fix this.

Running my LoD images in epsxe and pSX
They both break down in the same screen.
[CENTER][CENTER]Sony Computer Entertainment
Presents[/CENTER][/CENTER]

System Specs:
Sony Vaio VGN-FS640/w
Pentium M 1.6 ghz
1.0 GB ram
Intel 915GM Integrated Graphics (eww)

I suppose that's everything relevant specs wise.

Stuff I've tried:
Several different bios (probably touchy, not sure if I can specify more than that here)

GPU:
Petes OpenGL2
"     MesaGL1.76 (one that works best)
SDL 

The SPU always worked, so I left that be.

I also tried patching it, because before the patch I'd get the 1-800 screen in pSX.

Running epsxe 1.6, pSX 1.13.

Any ideas?

BTW, I was able to run these ROMs on the windows version of epsxe.

---

### Post by acoustibop on 2008-05-17
Which version of Legend of Dragoon are you using, Scrubzilla?  AFAIK copies of Legend of Dragoon are usually protected, but the protection varies according to whether you are using an NTSC or a PAL version.

If you're playing from CD, it's necessary to be able to read the subcode on the CD to be able to defeat copy protection; if you're playing from CD in pSX (I'm not sure if PSEmu CDR plugins for Linux have the same roundabout subcode reading facilities that some Windows ones do, but pSX can read subcode directly) you need an optical drive that's capable of reading subcode.  A PAL version should play directly if this condition is met as the CD will be copy protected, but for the mod protection on an NTSC version, you also need to use a PAL BIOS I don't think anyon's figured out why, but it works.  See the [Running Copy-Protected Games]("http://psxemulator.proboards54.com/index.cgi?board=support&action=display&thread=488") thread on the official pSX forum.

If you're playing from images, the images must include the subcode from the CD.  This means that they must have been ripped to either the CloneCD .ccd/.img/.sub or Alcohol .mdf/.mds format - unfortunately, ther are no applications for Linux that can rip to either format, so you'll need access to a Windows machine to rip to them.  Ripping is the only reason I still keep a Windows partition going... :(

And, again, in pSX, with good rips including subcode, copy protected images (PAL) should play directly and mod protected images (NTSC) will need a PAL BIOS to play.  Again, I don't know whether there's any way to play these in a PSEmu plugin emulator (eg ePSXe).

Another alternative is to find a patch for your image.  [MegaGames]("http://www.megagames.com/") is a good place for patches; but must must make sure that you get the correct patch for your version of the game, and you must have a good rip or it won't work.  A correctly patched image should play in ePSXe or pSX.  Bear in mind that not all patches work; don't delete your original unpatched image until you're sure the patch has worked Ok.

---

