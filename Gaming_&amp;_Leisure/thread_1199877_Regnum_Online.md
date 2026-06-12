---
title: "Regnum Online"
date: 2009-06-29
forum: Gaming &amp; Leisure
---

### Post by wolfyking2 on 2009-06-29
Ok, I have a weird problem with it.  I can't run regnum natively, but I can run it in wine.  I was thinking about posting in wine, but wasn't sure.  Anyways, the game is at like, 7 fps in wine.  Intel graphics, I know, I know.  I tried lowest settings, that bumped it up to like, 9 fps.  I was wondering if there are any fixes/tweaks? Thanks!

---

### Post by magmon on 2009-06-29
I made a post on the unofficial .deb installer, try installing it through that. It will be a native install, and will be found under games after it finishes. You may have to tweak with the game settings to make it work properly.

---

### Post by wolfyking2 on 2009-06-29
Um, thank you, but that's not what I mean.  When I try to run natively, It gives me the error saying, "your video card is not supported".  In wine, it doesn't.  But, in wine, it's really slow.  So I was wondering if there are some tweaks or guides out their that could help me boost the fps.  Somewhere around 30-40 fps will be plenty for me!

---

### Post by LinuxGamer on 2009-06-29
Well, looking at Regnums Website, I am going to guess your problems stems from this:
Regnum Online supports a wide range of video cards.
The following cards have been tested succesfully with the game:

ATI video cadrs
- ATI Radeon 7500
- Recommended: ATI Radeon Series 9500 or superior

nVidia video cards
- nVidia GeForce Series
- Recommended: nVidia GeForce Series 6x00, 7x00, 8x00


The following cards are still on a experimental stage. This means that we still didn't have the chance to test them properly. You could possibly play with these cards but there maybe glitches or unexpected crashes in some cases:

- S3 Unichrome/Delta Chrome (on-board and off-board versions)
- Intel 845/915/945/965 (on-board)
- Intel GMA 950/3000 (on-board)
- Matrox Parhelia
- XGI Volari/V3/V5/V8/Duo
- SIS Xabre

The following cards are not supported and there probably will never work with Regnum Online:

- nVidia TNT Series
- ATI Radeon 7200 and previous (i.e.: Rage)
- Intel 815 and previous
- Trident Blade 3D
- SIS old video cards

---

### Post by LinuxGamer on 2009-06-29
You may also want to look at [this thread ]("http://www.regnumonline.com.ar/forum/showthread.php?t=44326")for some ideas on getting the Linux version to run. Here is another thread to make the [native work]("http://www.regnumonline.com.ar/forum/showthread.php?t=36637"). And last but [not least]("http://regnumonline.com.ar/forum/showthread.php?t=31371").

---

### Post by hikaricore on 2009-06-30
> **hikaricore said:**
> Yes just like every other game you've had trouble with it's your intel "graphics" hardware.

^ Per my post in your last thread.  These games are too much for your system.

---

### Post by wolfyking2 on 2009-06-30
Yea probably ;) but Hey, I try!

---

### Post by wolfyking2 on 2009-06-30
> **LinuxGamer said:**
> You may also want to look at [this thread ]("http://www.regnumonline.com.ar/forum/showthread.php?t=44326")for some ideas on getting the Linux version to run. Here is another thread to make the [native work]("http://www.regnumonline.com.ar/forum/showthread.php?t=36637"). And last but [not least]("http://regnumonline.com.ar/forum/showthread.php?t=31371").It worked :o  But the problem is it only runs at like 10 fps on lowest settings :/  So are there ANY tweaks out there that would make this game run at at least 30 fps?

---

### Post by wolfyking2 on 2009-06-30
Actually, the game probably runs at 30 fps at spots, but when I'm near bulidings, some of those ice things, etc, it goes down a lot!  I was wondering why.  And when I quit the game, my desktop becomes like, really small.  I can only see like 1/8th of it.

---

### Post by nymusicman on 2011-08-13
If you have an intel card that is capable. Download driconf

sudo apt-get install dri conf

and turn on S3C (something like that). It will run just fine after that. Although you may have to tweak settings for smoothness.

If you have an Nvidia or ATI card. Make sure you are using the proprietary and not open source drivers for those cards.

---

### Post by Omegus on 2011-08-13
my question is how do you register with them so I can login?

---

### Post by Idaho Dan on 2011-08-14
Omegus,
go to [http://www.regnumonline.com.ar/index.php?l=1&sec=0]("http://www.regnumonline.com.ar/index.php?l=1&sec=0")

---

