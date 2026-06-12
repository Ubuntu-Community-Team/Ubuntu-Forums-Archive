---
title: "Problems building StepMania 3.9 final on AMD64 system"
date: 2006-02-09
forum: Gaming &amp; Leisure
---

### Post by flamepanther on 2006-02-09
Hey everyone.  I'd like to preface this by saying that I am, as you might expect, new to Linux.  To my own credit, I've been getting comfortable with the terminal fairly quickly (having a lot of DOS experience has helped with that), I've checked Google and searched teh forums for every bit of information I could find before posting here, **and** I've almost got the game to build correctly now.  I'm also not a programmer, or I could no doubt fix the problem myself more quickly than I could get help.

Obviously, the official binary on StepMania's home page doesn't work in 64-bit.  The source also doesn't configure correctly as-is.  I've applied the changes in the patch that was posted in [this thread]("http://ubuntuforums.org/showthread.php?p=660477") and that allows configure and make to work.  The compiled game runs fine (when added to the data files from the binary distribution), but displays only a black screen when attempting to display background videos.  The game's error log contains this:> WARNING: Unknown movie driver name: FFMpegWhich normally means that I don't have the developer libraries for FFmpeg installed.  I believe those would be libavcodec-dev and libavformat-dev, of which I have the latest versions for AMD64 Ubuntu, but StepMania doesn't see them.  In [this thread]("http://ubuntuforums.org/showthread.php?t=69144") it's suggested that I need an older version of FFmpeg to fix this, but the suggested version of FFmpeg doesn't seem to exist for AMD64 systems.  I also noticed this in the terminal during configure > checking for library containing avcodec_init... no
checking for library containing guess_format... noI assume that's basically the same problem.  It's looking for the FFmpeg developer libraries and can't find them.

I'm lost at this point.  Can I fix this with symbolic links?  Does something in the StepMania source need to be changed to get it to see the libs?  Do I need to find a different build of the FFmpeg libs entirely?  A combination of the above?  Any help would be greatly appreciated.

---

### Post by handy on 2006-02-10
Sometimes we are stopped by the 64/32bit problem.

As may or may not be the case with your problem here!

I changed to 32bit Breezy & never looked back, much easier & more things are possible to do.  I will continue to look at the 64bit Ubuntu's as each new version comes out, untill they are as capable as the 32bit.

This will happen inevitably! :p

P.S, I don't notice any speed difference on 32bit as opposed to the 64!

---

### Post by flamepanther on 2006-02-10
I can understand your point, since I already tried Windows XP x64 edition on my Windows partition, got fed up with it, and switched back to the 32-bit version.  However, having a 64-bit environment was one of the main reasons I decided to install Ubuntu on a second partition.  In particular, I wanted to be able to use 64-bit builds of the GIMP.  Mission accomplished there, so I won't be abandoning Ubuntu any time soon, but if I want to play 32-bit Stepmania I can just boot back to Windows.

That said, there has to be a way to fix this somehow.  Other programs that use FFmpeg have been converted to AMD64 successfully.  Like I said before, I'm not a programmer, but it looks to me like either the libraries aren't where StepMania expects them to be or they don't act the way StepMania expects them to.  If it's the former, I'd just need to know how to set up the appropriate symbolic links.  If it's the latter, then it seems like maybe it could be fixed if someone could successfully compile an older version of FFmpeg for AMD64 (I've had no luck trying to compile it myself).  At worst, the code in StepMania that needs the FFmpeg libraries could be updated.  I'm not expecting anyone here to do that (although we DO have the source code available), but other people have reported this problem to the StepMania developers, and they've responded that it's "not a bug".  I don't know if they think it's the fault of the people trying to compile the game and don't know that their outdated version of FFmpeg doesn't exist for AMD64 or what, but maybe if we can demonstrate that we've exhausted all other options they'll think about fixing the problem in version 4.0.  Or maybe someone else could fix it after all and send the SM developers a patch.  I was under the impression that was one of the advantages of open-source sofware. ;)

---

### Post by handy on 2006-02-10
The major hurdle here, is that we are in transition form 32 to 64bit hardware & OS's.  VERY few games have ever been written to run on 64bit.  (I have UT2k4 which is one of them).  

I would expect that as m$ vista, infiltrates the computer world in the not too distant future, that this will be the major push in the world to 64bit, just as win95 really started the 32bit change for the majority of users over a decade ago.

I think that in a few years, we will have mostly forgotten about 32bit, just like we've forgotten about 16bit!

At least I will have, I don't have a very good memory! :mrgreen:

---

