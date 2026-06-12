---
title: "PSone &amp; PS2 Emulator Help Please"
date: 2008-08-31
forum: Gaming &amp; Leisure
---

### Post by bipolaric on 2008-08-31
hi people, I have just downloaded PCSX Via Synaptic Package Manager, but I don't know how to use it, also, I am looking for a PS2 emulator to run my PS2 Games but I dont know where to find one or even compile it from source.  The last time i tried compiling from source I had to wipe my PC and re-install Ubuntu coz I messed it up, not knowing what to do.  I would like to add that I do actually own both a PSone & PS2, plus the games to go with them, I'm not a ROM pirate.  It's just, with the problems I have had installing certain games via wine, and EVEN Cedega, have left me somwhat dissapointed.  If I can play my PSone & PS2 Games on my Ubuntu, I need never go back to windows again.  If anyone can help me, please explain how to do things as if you were talking to a chimpanzee as I am a COMPLETE noob when it comes to compiling/installing from source/binary packages.

Please Help Me........Thanks For Reading This Post - Mark

P.S. - I have just downloaded pcsx2-0.9.4.tar.gz (saved as a file on my desktop) - But I haven't a clue what to do with it....Also does the PS2 Emulator play PSone games too, just like the console ?

ALSO, I have downloaded psemu-drive-cdrmooby also via synaptic, which rips the PSone games to the hard drive, but it doesn't show up in my menu as having been installed....It's just not there, why is this ?

---

### Post by dfreer on 2008-08-31
Some programs you install won't show up in the Menu, if they are generally designed to be used from the commandline.

PCSX2 is the only PS2 emulator for linux that I know of, and it's the best for windows too. Problem is, you need a really beefy computer to use it (My Core 2 Duo @ 2.0 Ghz isn't quite up to snuff) even in windows. 

As for the original playstation, there's ePSXe, PCSX, and pSX. pSX is great for accuracy and doesn't require a lot of setup/configuring plugins, so I'd recommend it first.

ePSXe and PCSX are great if you like enhancing the graphics of the original games, as they use graphics plugins and such. You should check out the various how-to's on this forum if you want to try those out.

I'm pretty sure no one has bothered incorporating PSX game emulation into the PS2 emulators simply because they haven't finished perfecting the PS2 emulators yet. pSX author supposedly is working on this though.

---

### Post by bipolaric on 2008-08-31
hi, thanks for your help, i tried the pSX for AMD64/i386 link, but it didn't have the correct comands for hardy heron, only gutsy & feisty.  What do i do next ?

I have downloaded pSX_linux_1_13.tar.bz2.....and when i open the package i get.....

A pSX folder in which is......bios, cdimages, pSX & readme.txt, (of which isn't very helpful) - What would you sugest I do next ?

---

### Post by dfreer on 2008-08-31
Yeah, my repository hasn't been updated for a long time, sorry I should've mentioned that.

Sounds like you downloaded pSX straight from the official website, if you didn't go ahead and do so here:
[http://psxemulator.gazaxian.com/](http://psxemulator.gazaxian.com/)

In either case, you will need to extract the .tar.gz file, and then you need to place the Sony BIOS file in the bios folder. You need to obtain this elsewhere as it is against the rules of this forum to post links to it.

Once that's done, make sure that the pSX file is executable (it should already be), then double-click it to launch it. It should ask you a few questions (prefered language and the name of that Sony BIOS file mentioned earlier), and then if all went well you should hear the familiar playstation boot-up noises and see the Sony Playstation logo.

If there is any problems with pSX, try running it in the terminal and see if it gives you any useful information there. One of the reasons I haven't updated my repository is pSX has been having problems with users using Ubuntu 8.04. It worked fine for me in all previous versions of Ubuntu but doesn't in 8.04, for some users it does work in 8.04 which is why I still recommend it.

---

