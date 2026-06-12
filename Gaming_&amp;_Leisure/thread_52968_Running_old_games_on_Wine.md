---
title: "Running old games on Wine"
date: 2005-07-29
forum: Gaming &amp; Leisure
---

### Post by steevc on 2005-07-29
About the only thing stopping me from dumping a Windows PC at home is that we have a few old games that the kids play sometimes. That PC runs Windows 98. My kids are still young and quite like these games:

The Snowman (Raymond Briggs book) - this runs straight from the CD.
Lego My World First Steps
Thomas and Friends - The Great Festival Adventure

So far I've installed Wine as described in their wiki. I tried running the Snowman game and got some errors

ALSA lib control.c:739: (snd_ctl_open_noupdate) Invalid CTL plug:hw:0
ALSA lib seq_hw.c:446: (snd_seq_hw_open) open /dev/snd/seq failed: No such file
or directory
fixme:mci:MCI_LoadMciDriver Couldn't load driver for type L"MUSIC".
If you don't have a windows installation accessible from Wine,
you perhaps forgot to create a [mci] section in system.ini

That last message repeated forever, but it did seem to be trying to load the game.

As for the others, I'm not sure where to start when it comes to installing them.

I've been using/programming computers for many years, but this is fairly new territory for me. I'll be grateful for any hints.

I should mention that I have wine 20050524 and have used winetools to install enough to run IE6, OE and WMP. That was impressive in itself.

Update: I've installed the Thomas game and that went smoothly. It says it needs DirectX 6.1, but that I already have something newer, but when I try to run the game I get

fixme:ddraw:Main_DirectDraw_SetCooperativeLevel (0x77c80cb0)->(00010022,00000015)
err:x11settings:X11DRV_ChangeDisplaySettingsExW No matching mode found! (NoRes)

Where do I go from here?

Thanks

Steve

---

### Post by BKonkle on 2005-07-30
I'm not sure how to help you on your problems, but I can tell you that I tried Wine for weeks, bouncing back and forth between official packages and the CVS versions, before I finally went all the way back to 20041019, and everything works perfectly for me.  I can run IE6, Dreamweaver MX, Photoshop 7, and more without any problems.

The instructions I followed were [here](http://www.ubuntuforums.org/showthread.php?t=52991&highlight=internet+explorer), and they very well might alleviate some of your problems.

---

### Post by christooss on 2005-07-31
What about runing games with dosbox

---

