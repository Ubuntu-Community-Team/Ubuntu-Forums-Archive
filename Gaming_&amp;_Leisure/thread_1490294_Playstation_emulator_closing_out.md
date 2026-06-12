---
title: "Playstation emulator closing out"
date: 2010-05-22
forum: Gaming &amp; Leisure
---

### Post by pr0t3g3 on 2010-05-22
epsxe closes out when I try to load the playstation 1 game diablo. I tried loading all 3 files and I even tried loading the whole folder itself but it wont load... it just closes the emulator out.

why is this and how can I fix it?


I probably should have noted this at the beginning, but I am running a linux based emulator just to clear that up so everything is supposed to be compatible


I am running ubuntu 10.04 (lucid) 

I have 497.1 mbs of memory and 1.4 gigs of swap

Not sure if that's enough; If I missed something please request it; I'd like not to have my post go unanswered because I didnt provide enough info.

---

### Post by pr0t3g3 on 2010-05-22
hmmm... it's less than 24 hours but... um.. bump?

---

### Post by portets on 2010-05-22
here's the emulator i use: [64-bit download]("http://pcsxr.codeplex.com/releases/37759/download/98572")          [32-bit download]("http://pcsxr.codeplex.com/releases/37759/download/98571")

works for me every time. and epsxe hasn't had a new release in 2 years. this emulator is still in ongoing development.

---

### Post by pr0t3g3 on 2010-05-22
> **portets said:**
> here's the emulator i use: [64-bit download]("http://pcsxr.codeplex.com/releases/37759/download/98572")          [32-bit download]("http://pcsxr.codeplex.com/releases/37759/download/98571")

works for me every time. and epsxe hasn't had a new release in 2 years. this emulator is still in ongoing development.It wont let me configure the controls for one and for 2 it wont run my iso...

---

### Post by El Lance-O on 2010-05-23
Is it just an .iso file, or is there .bin/.cue? You said you tried 3 different files...

Go back to the other thread we had going, and install pSX, that should work for you just fine, if not, try burning the .iso to a disk, and try running it like that.

---

### Post by pr0t3g3 on 2010-05-23
> **El Lance-O said:**
> Is it just an .iso file, or is there .bin/.cue? You said you tried 3 different files...

Go back to the other thread we had going, and install pSX, that should work for you just fine, if not, try burning the .iso to a disk, and try running it like that.
I thought I made it clear in pm's that I realized it's the emulators and/or it's configuration ( I don't see how though)  I was able to search for the .iso however, upon selecting it the emulator crashed/dissapeared. It won't even let me load from disk; it closes out immediately.  loading from disk is out.  I'll try psX

Edit: Well, I guess that's it, then.  The only one that works is psX, And that one skips like theres no tomorrow.

---

### Post by hikaricore on 2010-05-24
Might help if you posted terminal output or log files from the program in question.

---

### Post by pr0t3g3 on 2010-05-24
> **hikaricore said:**
> Might help if you posted terminal output or log files from the program in question.anthony@anthony-laptop:~$ pSX
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
cuebin: No .cue file found!  Will attempt to guess format assuming single track
cuebin: Unable to guess format
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
sound: underrun
/usr/bin/pSX: line 7: 13837 Segmentation fault      ./pSX

T_T It closed out when I tried to run the .Iso when  I started psx in terminal.  When I run it normally it just freezes when It shows the second playstation symbol just before the game would run it's own pre-dialogue.

---

### Post by pr0t3g3 on 2010-05-31
I'd nearly forgot about this thread.... but I still want playstation so BUMP

---

### Post by fallenshadow on 2010-05-31
Looks like its crashing because its missing a .cue file.

You could try installing: AcetoneISO.

As I think it has a feature to generate .cue files. However im not sure does it support that feature for .iso files.

---

### Post by pr0t3g3 on 2010-05-31
> **fallenshadow said:**
> Looks like its crashing because its missing a .cue file.

You could try installing: AcetoneISO.

As I think it has a feature to generate .cue files. However im not sure does it support that feature for .iso files.
Ok, I'll try that out, thanks! but if it still doesn't work is there an alternative?:confused:

I'm not really sure, what to do with this...

---

