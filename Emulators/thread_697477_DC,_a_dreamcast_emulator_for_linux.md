---
title: "DC, a dreamcast emulator for linux ?"
date: 2008-02-15
forum: Emulators
---

### Post by frenchn00b on 2008-02-15
It looks that very is none from zophar

---

### Post by RemmyLee on 2008-02-15
[lxdream]("http://www.lxdream.org/")

---

### Post by frenchn00b on 2008-02-15
> **RemmyLee said:**
> [lxdream]("http://www.lxdream.org/")

I compiled it, thanks I just made a DEB of lxdream
[http://www.megaupload.com/nl/?d=40LY7DRV](http://www.megaupload.com/nl/?d=40LY7DRV)

---

### Post by frenchn00b on 2008-02-15
> **RemmyLee said:**
> [lxdream]("http://www.lxdream.org/")

if I understand well, one need bin files with it ??

---

### Post by Sniffer on 2008-07-22
Thanks for your deb file, i will test it.

---

### Post by NxZDr on 2008-07-22
Cool, I'll keep this in mind if my Dreamcast ever dies. How well does it emulate?

---

### Post by shamusl on 2008-07-23
Maybe I'm a complete noob, but the deb isn't doing anything for me. Is this working for anyone else?

---

### Post by BigSilly on 2008-07-23
I tried this a while ago, but I couldn't get it to do anything/ I just put it down to the fact that I have a pretty dated PC. Looks like that might not necessarily be the case...

---

### Post by evets25 on 2008-07-23
> **frenchn00b said:**
> It looks that very is none from zophar

FYI, zophar.net is no longer being actively maintained, so any recent emulators won't be on there, and info on other emulators will be wildly out-of-date. It hasn't been updated in *years*. 

Ah, but I remember when it was THE place to go for emulators. Those were the good 'ol days, yep. I remember when it reached 1 million page views, as well as when it hit 2 million. And back then, that was a LOT!

EDIT: OMFG I just checked the zophar.net website, and it's baaaaaaaack! Hoo-ray! rejoice! This is the best news I've heard in a loooooong time! :D

---

### Post by GSZX1337 on 2008-07-23
> **NxZDr said:**
> Cool, I'll keep this in mind if my Dreamcast ever dies. How well does it emulate?

[COLOR="Blue"][Here]("http://www.lxdream.org/forums/viewtopic.php?t=35")[/COLOR]'s a crappy compatibility list.

---

### Post by raj7095 on 2009-09-01
Sorry for bumping into an old thread, but can you play games using a joypad with it.

---

### Post by 569874123 on 2009-09-06
> **raj7095 said:**
> Sorry for bumping into an old thread, but can you play games using a joypad with it.

You can do that with nulldc

---

### Post by beliyyal on 2009-09-27
Hey guys, I was wondering if anyone would help me out with something. I got lxdream, installed it fine and everything, but it does not run. I get the following errors in terminal:
> lxdream: could not connect to socket
lxdream: No such file or directory
05:00:19 00000000 WARN  Could not initialize LIRC.  LIRC hotkeys will be disabled.
05:00:19 00000000 WARN  Failed to load plugin: '/usr/lib/lxdream/input_lirc.so': Initialization failed
05:00:19 00000000 ERROR Unable to load file '/home/dalton/.lxdream/dcboot.rom': No such file or directory
05:00:19 00000000 WARN  Unable to load file '/home/dalton/.lxdream/dcflash.rom': No such file or directory

it opens the lxdream window, but says "Unable to create render buffers (requires either EXT_framebuffer_object or GLX 1.3+)" followed by "Video driver 'gtk' failed to initialize (could not connect to display?)". Does anyone have an idea on how to fix this?

---

### Post by NeoZiggy on 2009-11-10
The file "dcboot.rom" is the needed Dreamcast BIOS. It is needed to play games, however (insert legal mumbo jumbo here) you will have to search google for something like "dreamcast bios" and find it yourself. You may have to rename .BIN files to .ROM and place them in your '/home/USERNAME/.lxdream/' directory.

I did not see any video error messages, Soul Calibur ran but very slow.

BTW: Their website has a newer version then shown in this forum, with a DEB package to make things easy. [http://www.lxdream.org/]("http://www.lxdream.org/")

---

### Post by Nick_Jinn on 2010-07-28
Is it ok to resurrect still relevant threads? I would love a dreamcast emulator.

---

### Post by Perfect Storm on 2010-07-28
> **Nick_Jinn said:**
> Is it ok to resurrect still relevant threads? I would love a dreamcast emulator.

It's close call for necro lock - especially when you haven't added anything to the thread. But I'll let stay open for now.

---

### Post by Nick_Jinn on 2010-07-28
Well I tried installing that deb and it said 'wrong format'. I wonder if I am missing some files or if its really just not compatible. Other people in 2008 seemed to have installed it at least.

---

### Post by bridabom73 on 2010-08-11
> **Nick_Jinn said:**
> Well I tried installing that deb and it said 'wrong format'. I wonder if I am missing some files or if its really just not compatible. Other people in 2008 seemed to have installed it at least.

I got that too because it was a 32 bit .deb and I run a 64 bit system. Just go to the link in the second post and on the left side of the page, click Downloads and download the correct .deb file. Now it installed correctly for me. I still have yet to actually try the emulator.

---

### Post by Nick_Jinn on 2010-08-12
Does it play Soul Calibur?

---

### Post by brantpadams on 2011-09-10
I know this thread's a little old, but I was hoping for a little help with lxdream. 

I have it installed and I can get it to run, but it's extremely sluggish. It only gets through the opening dreamcast logo and the time and date prompt, after that it won't load the game I'm trying to run. I'm pretty sure it's a problem with the video settings, but for some reason I'm unable to access the the video or audio settings for the emulator. They're simply grayed out in the dropdown menu. 

Anyone know how I can get into the settings? I'd at least like to see if it'll run a game decently.

---

