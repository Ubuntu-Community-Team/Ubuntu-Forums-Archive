---
title: "Need help with emulator plugins."
date: 2007-08-24
forum: Gaming &amp; Leisure
---

### Post by nrgenova on 2007-08-24
Hi. I've been running epsxe and mupen64 on Gentoo for years with no issues, but now that i've just switched over to Ubuntu, I can not for the life of me get my emulator plugins to work.

I am having the same issue with every single Linux plug-in for both emulators. The cfg executables will not open. I have tried them both in the emulators themselves, and independently from the plug-ins folders. When I run them in a console, I get no error message. It simply will not open the window.

The plugins are the only thing on my pc that I can not get to open. I am certain that the permissions are set correctly, and the files are set to executable. And if anyone is wondering, yes they are the linux plugins and not the windoze alternative. Does anyone have any idea what could cause this?

---

### Post by acoustibop on 2007-08-24
I don't know about N64 emulators, nrgenova, although I seem to have got Mupen64 running Ok.  But for Playstation emulators, I'd recommend [pSX Emulator]("http://psxemulator.gazaxian.com/") rather the ePSXe.  For a start, it's pluginless; in a standard Ubuntu installion, you just need to add libgtkglext1 (in the repositories), a Playstation BIOS and games, and you're good to go.  IMHO pSX is superior to ePSXe in Windows, but in Linux it's no contest; a doddle to install and runs far better than ePSXe or PCSX.

---

### Post by nrgenova on 2007-08-24
In all of my years of programming and playing console emulators, I have never heard of PsX Emulator. I guess that would be because I have never had a need to, since epsxe and pcsx have always worked perfectly for me. I will definitely give it a try. Maybe it will surprise me.

As for the plug-ins, I really don't think it has anything to do with the emulators themselves. They work fine. I have a feeling that my setup is just missing some obvious package, something I should have caught but didn't. Although I am thoroughly enjoying the simplicity of Ubuntu after using Gentoo for so long, I am finding that I am having MANY more problems getting everything running on it than I ever did with Gentoo. 

I guess Portage just spoiled me.

Edit: pSX seems to work fine, but my i845 integrated video cant handle it. Maybe i'll give it another try when I get my NVidia card fixed. In the meantime, I really need to get these plug-ins working!

---

### Post by disturbedite on 2007-08-24
uh, the reason you prolly haven't heard of it (pSX) is cuz its newer.  but yeah, it is definintely recommend OVER pcsx & epsxe in my book.

i don't know what problem you're having but i have the same card (intel i845g) and it works fine with mine!  no way would i ever go back to epsxe or pcsx.  its just great that there is finally a psx emulator where you don't have to worry about ridiculous plugins.

---

### Post by nrgenova on 2007-08-24
Well, I stand corrected. Something must have been eatting up my memory. Upon a reset, pSX is working great

If it has excellent compatibility, I might just start using it. It has been centuries since the prior two have been updated, and I usually try to stick with what's still in progress.

Thanks for the advice! it may not have directly solved my problem, but it was most definitely helpful info =]

---

### Post by disturbedite on 2007-08-25
good idea to stick with what's still in progress.  i'm the same way.  :)

---

### Post by acoustibop on 2007-08-25
Apparently, pSX' compatibility is now considered to be better than anything else except Connectix VGS.  However, I can't confirm that from personal experience; it's from someone else's quote.

I can say that pSX runs every single Playstation game I've tried on it; I'm looking at about 25+ games I have on my shelf.  It is necessary to make sure you have a good rip (preferably .ccd/.img/.sub or .mds./mdf, as these include subcode from the original CD) if you're playing from images for some copy or mod protected games, but pSX is very good on these.

I just got myself a copy of Final Fantasy IX (PAL), which is not only copy protected, but the protection is, apparently, notoriously difficult to break: I was getting frustrated trying to play it from CD or get a good rip.  Then I changed from using my DVD-ROM to my DVD-RW (-RW drives generally read a wider range of formats than -ROM ones) and no problem!  It would play straight from CD and I had no problems making a good rip.

So the moral is: compatibility in emulators is dependent on more than the emulator's capabilities; you need a good optical drive, as well! ;)

---

### Post by DoktorSeven on 2007-08-25
pSX is a lot slower than ePSXe and has about the same compatibility in my experience, so I always recommend ePSXe over pSX.  Plus when I tell pSX to go fullscreen it cuts off the bottom of the screen... :(

  I've had no problems with using ePSXe and its configuration windows, so I'm not sure what to tell you there.

---

### Post by disturbedite on 2007-08-25
and i've not experienced those problems with pSX DoktorSeven.  i've actually found it faster than the other ps1 emulators.

---

### Post by Sockerdrickan on 2007-08-25
pSX wins

---

### Post by acoustibop on 2007-08-25
I've found pSX to be both faster (and much more free from slowdowns; not the same thing) than ePSXe; also it seems to require much less CPU power.  Nor have I had any problems with the full screen display; in fact the only problem like that I ever have with it is that the Windows version tends to wander around the screen and sometimes winds up a bit off it.  But since I'm not using Windows any more except for ripping (the only programs that will rip to .ccd/.img./.sub or .mds/.mdf are Windows exclusive...) that doesn't exactly worry me.

I can't say I've come across any other Linux users with these problems, either.  I would suspect the cause must be somewhere else than pSX, DoktorSeven.

---

### Post by DoktorSeven on 2007-08-25
It's nuts that only I have these issues.  No other applications/games/emulators/etc have this sort of issue, and it's not just this computer or Linux, I have ran pSX on Windows before on other computers and ePSXe still runs faster and better for me.

---

### Post by acoustibop on 2007-08-25
Are you running ePSXe with FPS limit enabled and on autodetect, and no Frame skipping, DoktorSeven?  Otherwise, you should try running pSX with the Fast forward key held down, VSync off and, if appropriate, Frame skipping on to compare speeds... ;)

---

### Post by DoktorSeven on 2007-08-25
Nah, it's just that several games that run fine on ePSXe skip and stutter in pSX.

I dunno, I get the impression that people don't properly configure ePSXe with good plugins or something.

---

### Post by acoustibop on 2007-08-25
There are bound to be some games that run better on ePSXe than pSX.  Nevertheless, the majority of users' experiences seems to be that pSX runs more games faster (in the sense that it runs them continuously at the correct speed) and with less CPU usage than ePSXe does.

FWIW I spent 6 or 7 years using ePSXe in Windows, and was pretty happy with the result.  Until pSX came along, that is.  Even in the first version or two (this was in Windows), it was clear that it had a lot going for it that ePSXe didn't have, although at that point it was still pretty rough.  12 versions later (and still developing) it seems to me that it's drawn far ahead of ePSXe - and now there are Linux versions, as well.

Have you managed to get analog controller support working in ePSXe in Linux, and if so, how?

---

