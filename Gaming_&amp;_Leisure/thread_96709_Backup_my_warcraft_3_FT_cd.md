---
title: "Backup my warcraft 3 FT cd?"
date: 2005-11-29
forum: Gaming &amp; Leisure
---

### Post by polpak on 2005-11-29
I need to make a backup copy of my War3 FT CD. My original is looking rather worn and I'm afraid it'll need to be replaced soon. Since Warcraft is one of the few games that actually works on my shiny new linux only system I'd be sad to see it go.

Can anyone recommend software for making a workable backup copy of it? I've tried K3b and some others, but the warcraft game always prompts for the cd when I start it under wine (the original disc works fine). I don't want to use a no cd crack because it's not legal (at least not in my country) and it can also mess up my ability to play online.

Anyone have any helpful hints?

---

### Post by Remmelas on 2005-11-29
We'd have to research the cdrecord man pages, but if your burner supports reading and writing in RAW mode, it is possible to make 1:1 backup copies of your game disk.  usually to make a perfect copy of a protected game disc it involves researching to see what options are necessary to copy the protection, then reading man pages to find out how to enable those option... I've never done this with cdrecord, but have done it with Nero Burning Rom in windoze on my wife's pc(hers is the one with the good cd burner anyway)

---

### Post by polpak on 2005-11-29
Well according to K3b it does support all the raw formats, as well as DAO and TAO.. Any ideas on what options I need to specify? 

I've also tried various cdrecord guis, and even running cdrecord command line, but it seems to only work with scsi burners or you have to load ide_scsi and I couldn't really get that working.

Since K3b also uses cdrecord internally, it should work right?

---

### Post by Remmelas on 2005-11-29
I'm stranded at work right now, so I can't fire up k3b and see what is there.  So long as K3b supports passing the correct options to cdrecord, it should support anything that cdrecord does.  According to cdrecords man page, the -clone option used in conjunction with the -raw96r modes should allow all subchannel data to be written(it's usually in the subchannels that cd's get protected).  cdrdao is actually the binary that supports the raw modes necessary, and is included with cdrtools(along with cdrecord).  

I've been googling unsuccessfully to find instructions on enabling the reading and writing of subchannel data necessary to achieve what you need to do, but can't find any answers, and am hours away from being able to look at it on my own machine.

---

