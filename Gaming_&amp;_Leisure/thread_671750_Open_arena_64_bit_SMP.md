---
title: "Open arena 64 bit SMP"
date: 2008-01-18
forum: Gaming &amp; Leisure
---

### Post by High_Yield on 2008-01-18
Hope I'm posting this in the right place...

I've seen instrucitons for two versions of Open Arena which I could possibly use since I have an AMD X2 4600+ (which is a dual core):
- The 64 bit version
- The SMP version

So - is there a "64 bit SMP" version?

Any suggestions are welcome.

(I could also easily post this in the 64 bit forum but will likely get more hits here).

Thanks in advance - B

---

### Post by DoktorSeven on 2008-01-18
My download from their site has a "ioquake3-smp.x86_64" binary; I think that's what you'd need to run.

---

### Post by High_Yield on 2008-01-19
Thanks Dok but...

I think Open Arena already came with my 64 bit install of linux - so...
a) I don't see the file you're talking about
b) I cannot get to the open arena site - always down lately
c) If I do a /cvarlist I can see at startup that I turned the SMP option on, and OA barked at me in a yellow font saying "SMP was disabled at compile time"

So - how did you get the file you're talking about, and what did you do with it ?

Any help is appreciated - I will click your thank button is 10 seconds here..

- B

---

### Post by DoktorSeven on 2008-01-19
The OpenArena that comes with Ubuntu is an older version, so it's recommended to go grab the one from the OpenArena site, even if it's a pain sometimes to get the file.  I have no idea whether or not the version available in the repositories even has that file, but in the file you download and extract from the OpenArena site, there are several binaries that you can run to start OpenArena, and that's one of them.

When you extract it you can either doubleclick it from a file browser or go to the directory in a terminal and do ./ioquake3-smp.x86_64

---

### Post by High_Yield on 2008-01-19
Thanks again Dok...

I am using that one file now as you suggested and it does run without the smp error - but it does say a different warning, that smp "failed" or something - if you look at the beginning of a /cvarlist command.

So, does that actually run in SMP mode by default or are there still issues do you think?

Regardless, thanks again for your help.

- B

---

### Post by DoktorSeven on 2008-01-19
Have no idea, really.  Never tried to run anything in SMP since I don't have any computers with SMP.  I'm stuck on single-proc 32-bit :).  Not sure why it would say it failed.  If anyone else here runs OA on 64bit/SMP, maybe they can give you some insight.

---

### Post by dag123sapir on 2008-01-19
you can go in to the synaptic and download open-arena that gonna be not the latest version but after you download that version in the game it should ask you to download that latest version of the game

---

