---
title: "Can someone help me get Baldur's Gate II running w/ wine?"
date: 2006-03-27
forum: Gaming &amp; Leisure
---

### Post by glassgloss on 2006-03-27
I have bg I running.

When I insert the BG 2 cd's my reader has trouble deciphering them, and the discs just show up w/ two files in them, and their names are a bunch of gibberish.  I have got them to read them before, however, and run the setup.exe like normal.  however, once it loads the setup screen doesn't have any words on it--it is just blank and strange.  I don't want to get it with cedega and all the instructions I find are for that.

Thanks,

---

### Post by glassgloss on 2006-03-29
nobody knows why my cd drive cannot read these disks?  they have problems with icewind dale discs too, but not much else

---

### Post by glassgloss on 2006-03-29
I don't mean to keep bumping this thread, but I wanted to throw out the error messages I am getting to see if that might help:

right after it loads the setup, this pops up: Internal Failure Error number: 0x80040707

then the next screen comes up, containing text, but missing the logo on the left,

then the license agreement comes up... but there is no text

then when it asks for the type of setup I prefer (minimum, complete, etc) the box is empty and I cannot select one... followed by an "unknown error" and then it crashes.

---

### Post by Pablo El Vagabundo on 2006-03-30
TBH it sounds like your disks are wreaked.

Do you have another computer to try the CD's in? Somtimes CD writers can read the CD's better.

Or if you have windows installed try and load the disks there.

If you can read them on another machine try and make a complete copy and try install them.

I have BGII at home although i have never tried it under wine.

Hope this helps.
Pablo

---

### Post by Toxicity999 on 2006-03-31
That happened to me occasionaly when I had my CD drive unlocked (Unmounting by pressing the eject button.) Of course this probably isn't your problem but anyway, try some of the more obscure methods, Toothpaste, car glass cleaner etc, all supposidly good for making the CDs readable again, if your REALLY desperate theres an article I got from digg on using some chemical to remove the plastic coating. Of course, thats geared more towards Personal CDs one can copy later.

---

### Post by charlieg on 2006-04-07
Have any of you tried running Baldur's Gate (I or II) using [GemRB](http://gemrb.sourceforge.net)?

---

### Post by Miguel on 2006-06-22
Does BG2 really work with GemRB? The site is down currently, but according to freshmeat last update took place on 2004. That seems a lot of time for linux. Anyway, I'm currently having trouble with wine and I'd like, no, I *need* to run BG2 under linux.

BTW: I've read at winehq that copying your BG2 install directory from windows will work.

---

### Post by vblanton on 2007-01-03
I am also trying to get baldurs gate 2 to run at the moment. First, I grabbed the latest wine, 0.9.28 because a couple Gentoo users gave a gold status for Baldur's Gate II Throne of Bhaal with it.  I ran the installer but it crashed with a ridiculous error:

Error Number: 0x80040706
Description: Object reference not set
Setup will now terminate

yaay! ... well damn. I was hoping for things to go a bit smoother. I've tried all three install types and they all exit the same way. not I'm going to attemp to use this to figure it out:
[http://cedegawiki.sweetleafstudios.com/wiki/Special:Search?search=baldur&go=Go](http://cedegawiki.sweetleafstudios.com/wiki/Special:Search?search=baldur&go=Go)

I'll post again if I get it to work...

---

### Post by Miguel on 2007-01-04
Hi vblanton,

I had BG2 working under Dapper... but I still have windows (yes, I know) so getting it to work was just copyiing the BG2 directory from windows to somewhere in linux (*trick:* you need not copy all the CD data, symbolic links will work perfectly and save a lot of space). It was some time ago, so maybe the "double cursor" issue has been fixed when 3D accel is enabled.

If you have a clean computer with no trace of Win XP, I'd guess you could try the Loki installers. They exist for both SoA and ToB. See [this link](http://liflg.org/?catid=7&gameid=18). If you have an european version of BG2, you'll probably have to use the german installer (I don't think the installer edits or translates files).

As a side note, if one feels especially adventurous, it might be possible to install BG1, BG2 on linux and then use BG tutu and play BG1 with the BG2 engine. It (more or less) works on windows, so maybe, one day...

---

### Post by Enverex on 2007-01-10
I wouldn't recommend TuTu to be honest. It felt like it took away some of the feel from the original Baldur's Gate and the 3rd Edition rules just made the game in itself a bit screwy. Baldur's Gate should work fine under Wine though. The second is unfortunately broken at the moment due to an issue with OpenGL layering. Basically the HUD/GUI and such get muddled up and the dialog windows are stuck below other parts of the windows. Hopefully it'll be fixed soon though.

---

### Post by Perfect Storm on 2007-01-10
I run Baldurs Gate 2 with this Loki installer (based on wine) - [http://liflg.org/?catid=7](http://liflg.org/?catid=7)

---

### Post by Miguel on 2007-01-11
> **Enverex said:**
> I wouldn't recommend TuTu to be honest. It felt like it took away some of the feel from the original Baldur's Gate and the 3rd Edition rules just made the game in itself a bit screwy.

Mmm... I'd bet BG2 uses AD&D 2nd edition. You know, the lower the AC the better, no feats, any one-handed weapon can be used as a left hand weapon... It's true though that 3rd ed classes inserted into BG2 (sorcerer) become playable under BG, plus some other freedom taken by bioware. But the core is still 2nd ed.

About tutu, yeah, it might take away some of the original game but some people find the original UI and fonts unbearable. What's more, 3D accel fixes some awful flickering present on my laptop when moving the screen over "shadowed" areas.

---

### Post by Enverex on 2007-01-11
> **Miguel said:**
> Mmm... I'd bet BG2 uses AD&D 2nd edition. You know, the lower the AC the better, no feats, any one-handed weapon can be used as a left hand weapon... It's true though that 3rd ed classes inserted into BG2 (sorcerer) become playable under BG, plus some other freedom taken by bioware. But the core is still 2nd ed.

About tutu, yeah, it might take away some of the original game but some people find the original UI and fonts unbearable. What's more, 3D accel fixes some awful flickering present on my laptop when moving the screen over "shadowed" areas.

It was 2.5nd edition wasn't it, not third, yeah sorry, bad memory. The res was low and it was a bit garish but I find that part of the charm of the original, just... something I don't like about how Tatu changes it. Felt... "wrong". The flickering is caused by the res and response time of your LCD, it happens on my laptop too, luckily not on my desktop though.

> **Artificial Intelligence said:**
> I run Baldurs Gate 2 with this Loki installer (based on wine) - [http://liflg.org/?catid=7](http://liflg.org/?catid=7)

If you use that you won't get any "official" support for Wine but it should 'hopefully' work because it uses a set version of Wine that used to work with Baldur's Gate 2. The current issue with BG2 is being worked on rather hard because it affects a lot of apps and is being largely re-written.

---

