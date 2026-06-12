---
title: "The 7th Guest"
date: 2007-02-07
forum: Gaming &amp; Leisure
---

### Post by Quiet Robert on 2007-02-07
I want to play The 7th guest again.  Is there any way to run it in Ubuntu Edgy?

---

### Post by rabid emu on 2007-02-07
Never heard of it, but I'll assume it's a windows game, in which case try Wine.

---

### Post by hikaricore on 2007-02-07
I remember there being a windows and dos version of the game, check the [wine application database]("http://appdb.winehq.org") for the game.  If you do not find it there it's probably the dos only which may be playable with dosbox.

Sadly I can't find my old copy of the game (still have the manual oddly enough) so I can't find out myself.  :/

---

### Post by tjotser on 2007-02-10
I will try this the next hour or so because i have the cd here with patch or some fix.
I'll be back...

UPDATE Ok i've tried it, i copied the second disk to a folder , accessed it from dosbox and started the game.
I get to the first screen where it asks me for Disc1, which it is not seeing. I read that it has to do with the mscdex or something that is required, or it could be my mount point ( media/cdrom0) ? i don't know ...
For now i give up.

--- WELL i got mscdex running by adding " -t cdrom" in dosbox but still no luck
here are some patches
[http://www.thealmightyguru.com/Reviews/T7G/T7G-Stats.html](http://www.thealmightyguru.com/Reviews/T7G/T7G-Stats.html)

---

### Post by xenophule on 2008-04-24
From what I've been able to do so far...

**WARNING** As of this post the game hangs once it's loaded, but it gets up and running.

First, create a folder in your home folder called DOSGAMES.
Next, run DOSBOX and put in the following:

```

mount C ~/DOSGAMES/
mount D /media/cdrom0
```

I, personally use my second CD ROM drive, so I use /media/cdrom1, so do whatever yours is.

Then, insert the second disc, type 'D:' which will switch you to the mounted CD drive and then type 'install'.

Select the C: drive to install to (which is your home folder/DOSGAMES/ folder). Keep pressing enter until your screen starts flashing. (WHOO SEIZURE!)

Next it asks you for the sound drivers. I go with the Windows Default one (or whatever it's called--at the bottom of the list). 

Once it's done installing, your directory should now be C:/ID/T7G>
Put in the first disc and type 't7g'

The game should load, you should see the Ouija board, and here's where it hangs on me. 

Hopefully it helps all y'all and maybe there's a work-around for this hanging problem.

---

### Post by grossaffe on 2008-04-24
ah, the seventh guest.  that name brings back fond memories.  Feeling a little... lonely?

---

### Post by sirdilznik on 2008-04-24
Wow that was an awesome game.  I still have my discs somewhere.  I should go find them and give this a try.

---

### Post by grossaffe on 2008-04-24
I never did play the eleventh hour...

---

### Post by fillintheblanks on 2008-04-24
that game gave me nightmares :-?

I hated going to the kitchen downstares absolutely hated it

---

### Post by newbjeff on 2008-04-24
I'm running Hardy and recently loaded both The 7th Guest and The 11th Hour and both seem to run OK under Wine.  In fact, The 7th Guest runs better there than on my Windows XP Professional machine.  

If you don't have it already, search for The Seventh Guest Direct-x and find the Direct-x package for this game.  I was unable to run the installer directly in Wine, so suggest you install the game on a Windows machine and extract the Direct-x package files into the game directory.  I then made a T7G directory in the Wine C: drive and copied everything from the T7G directory on the Windows machine to that.  Configure the application (winecfg) to start v32tng.exe in Wine as Windows 95 or 98, making sure the CD is shown under the Drives tab.  Start the game by double-clicking v32tng.exe or make a desktop launcher with the path to that file as the command.  Best of luck.

---

### Post by voteforcondit on 2010-05-13
anyway to install it with out installing on windows first?

---

