---
title: "Gnormalize"
date: 2005-10-18
forum: Deferred/Invalid Requests
---

### Post by sinbad782 on 2005-10-18
I haven't been able to find gnormalize anywhere in the repos. It would be useful to have this in universe or backports as I have a load of AAC/M4A files that I want to transcode into MP3. The homepage for the software is at:

[http://gnormalize.sourceforge.net/](http://gnormalize.sourceforge.net/)

---

### Post by sieczka on 2005-11-12
[QUOTE=sinbad782]I haven't been able to find gnormalize anywhere in the repos. It would be useful to have this in universe or backports as I have a load of AAC/M4A files that I want to transcode into MP3. The homepage for the software is at:

I'm all my hands and legs for it! Gnormalize seems to have everything needed:
1. CDA  extraction via cdparanoia
2. OGG, MP3, FLAC (and more) encoding
3. normalize funtcion, which is missing in all the SoundJuicer, Grip, other gui rippers I know., and which is a crucial funtcionality, needless to say
4. it's light
5. easy to use

Gnormalize should replace the default SoundJuicer IMO in Ubuntu.

Maciek

---

### Post by sinbad782 on 2005-11-14
Hi,  I did managed to install the deb that is on the homepage and all seems fine. but this was a pakage built for Debian stable and so I wasn't sure if it would work at the time. Decoding to WAV and re-encoding to MP3 and OGG work fine as long as you have the dependencies like faad, faac and lame etc.  

There are also rpm packages out there but I didn't try converting these with alien as I never seem to have much luck with this tool. 

In any case, this is a nice powerful tool and it would be nice to have it available in the Ubuntu repo trees - if it isn't already!

Cheers, PJS

---

### Post by Hamman on 2005-11-14
I would also enjoy seeing this in the repos.

---

### Post by mvandeg on 2005-11-21
[QUOTE=sinbad782]There are also rpm packages out there but I didn't try converting these with alien as I never seem to have much luck with this tool. 
[/QUOTE]

In this case
```
fakeroot alien --to-deb gnormalize-0.47-1.noarch.rpm
```
does the trick. It worked on my system.

---

### Post by jdong on 2005-11-21
Please take this up to the Masters of the Universe team (#ubuntu-motu on irc.freenode.net) -- I cannot add brand-new packages to Backports.

---

### Post by henriquemaia on 2005-12-12
Just for curiosity, is this app to be included on backports? 

I really like gnormalize and would enjoy very much to see it on the repositories.

Thanks a lot for all your work, Ubuntu Backports Team.

---

### Post by jdong on 2005-12-13
It first needs to enter Dapper's Universe to be eligible for backporting. Contact #ubuntu-motu or put it on the UniverseCandidates page on the Wiki.

---

### Post by Gomek on 2006-05-21
Any news on whether this is being added or not yet?

---

### Post by AustinMatherne on 2008-04-10
Any news on this?

---

### Post by robenroute on 2008-06-07
It would be nice to have proper packages, indeed. Especially with the latest 6.1 release: wavegain is required, but there are no .debs (I know, I know, everything is doable/compilable/fixable, but still...)

Anyone?

---

