---
title: "CD Ripping Speeds"
date: 2006-03-27
forum: Desktop Environments
---

### Post by Edward The Bonobo on 2006-03-27
I'm getting extremely slow ripping speeds with Soundjuicer.  I'm not sure if this is normal, or should I expect better?

It's a decent CD-RW drive, but in a low-end machine. (256MB, PII 333Mhz).  I have DMA enabled.  The speeds - I'm lucky if it gets as high as 1.3x.  1.1x or 1.0x is more usual.  Sometimes it starts up as high as 1.7x, then falls back again.  These are for .mp3s at 192Kb/s

It *seems* to work faster in xfce than in Gnome - but I haven't compared extensively.  And I *think * it's especially slow with scratched disks (which my drive doesn't cope with very well anyway).

My processor is working flat out while it's ripping (no surprise!).  Are the slow speeds just down to the processing required to encode to .mp3?  But I seem to remember getting better speeds in Windows.

Most importantly - are there quicker ways of ripping?  Another package, maybe?  (Or would It be more cost/time effective to just replace my CDs at $1.43 a time from [http://allofmp3.com](http://allofmp3.com) ;) )

---

### Post by TLE on 2006-03-27
[QUOTE=Edward The Bonobo]I'm getting extremely slow ripping speeds with Soundjuicer.  I'm not sure if this is normal, or should I expect better?

It's a decent CD-RW drive, but in a low-end machine. (256MB, PII 333Mhz).  I have DMA enabled.  The speeds - I'm lucky if it gets as high as 1.3x.  1.1x or 1.0x is more usual.  Sometimes it starts up as high as 1.7x, then falls back again.  These are for .mp3s at 192Kb/s[/QUOTE]
I'm not an expert on this but I think that with a 333MHz ripping speeds like that are probably normal. That being said, that doesn't mean that it can't get to work better.
[QUOTE=Edward The Bonobo]
It *seems* to work faster in xfce than in Gnome - but I haven't compared extensively.  And I *think * it's especially slow with scratched disks (which my drive doesn't cope with very well anyway).[/QUOTE]
That's very likely, xfce doesn't use as many system resources as GNOME
[QUOTE=Edward The Bonobo]My processor is working flat out while it's ripping (no surprise!).  Are the slow speeds just down to the processing required to encode to .mp3?  But I seem to remember getting better speeds in Windows.[/QUOTE]
Yes, it probably is, (see first reply) don't know about windows though
[QUOTE=Edward The Bonobo]Most importantly - are there quicker ways of ripping?  Another package, maybe?  (Or would It be more cost/time effective to just replace my CDs at $1.43 a time from [http://allofmp3.com](http://allofmp3.com) ;) )[/QUOTE]
Allright. Yes there deffinitely are other packages. If your are up for it I think you should try mp3c (It's available through Synaptic in Universe). It's a commandline utility but with a user interface (sort of like midnight commander), it takes a little bit of setting up but once it is set up it is very easy and fast to use. The big advantage here is that you can then free a lot of resources by not logging in graphically. So if you are up to it, install mp3c, set it up and get yourself familiar with it and then reboot and then instead of logging into GNOME or xfce, press ctrl-alt-F1 and log in at the commandline and use mp3c there, I think that should be faster.
Regards TLE
PS: I'll help you as much as I can with setting mp3c up if there's problems, I would just hate for you to have to pay for your own music once more ;)
EDIT: Wops I didn't see your bean count, I may have included a couple of unnescesary newbie explanations in there. Hope you don't mind

---

### Post by Edward The Bonobo on 2006-03-27
vmt.  I'll probably not get around to it for a while, but I'll bear you in mind.

> Wops I didn't see your bean count, I may have included a couple of unnescesary newbie explanations in there. Hope you don't mind

No offence taken.  My number of beans simply reflects the amount of flailing I've been doing.  Anyway - it's good that people are prepared to speak newbish.  It's how we learn!

---

### Post by jpkotta on 2006-03-27
I prefer abcde (A Better CD Encoder).  It's also non-GUI, actually it's a fairly readable bash script.  You write up a config file and just run abcde everytime you want to rip.  I decided to use it when I found that SoundJuicer would not let me rip more than 1 CDs at a time (if some one wants to know how I did this, PM me and I will write a quick howto).  My config file is attached for reference.

One more thing: you can try reducing your cd paranoia setting.  If you get skips in the output, increase it again (this will only happen if the CD is damaged).  You can set it by running gconf-editor and searching for paranoia.  This applies to SoundJuicer, not to all applications that use cdparanoia.

---

